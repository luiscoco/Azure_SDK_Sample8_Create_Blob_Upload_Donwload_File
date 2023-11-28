# Azure SDK Sample8: how to create an Azure Blob container and Upload/Donwload a file from/to your local hard drive disk

https://learn.microsoft.com/en-us/azure/storage/blobs/storage-quickstart-blobs-dotnet

### 1. Create an Azure Storage account

![image](https://github.com/luiscoco/Azure_SDK_Sample8_Create_Blob_Upload_Donwload_File/assets/32194879/8ba82175-1f6a-4fe1-a343-2caf8bc38f0a)

![image](https://github.com/luiscoco/Azure_SDK_Sample8_Create_Blob_Upload_Donwload_File/assets/32194879/f8cd86dc-3e22-4dcf-9b02-5e4ae91bee01)

### 2. Grant permission to the Azure Storage account for creating a Blog storage container

![image](https://github.com/luiscoco/Azure_SDK_Sample8_Create_Blob_Upload_Donwload_File/assets/32194879/1e424431-1f39-40b9-a7d5-80a75443c2be)

![image](https://github.com/luiscoco/Azure_SDK_Sample8_Create_Blob_Upload_Donwload_File/assets/32194879/183a78cb-3de8-4bd3-a998-99e5ed0af526)

![image](https://github.com/luiscoco/Azure_SDK_Sample8_Create_Blob_Upload_Donwload_File/assets/32194879/799a62de-7a48-4bd9-9927-d7b57cbfb96d)


### 3. Install **.NET 8 SDK** 

Download from https://dotnet.microsoft.com/en-us/download) and then we can access the **.NET CLI tools**

### 4. Create a new .Net 8 C# console application

Open in VSCode a Terminal window and run the following command for : 

```
dotnet new console --framework net8.0
```

### 5. Load the libraries for Azure SDK for .NET: **https://www.nuget.org/packages**

For loading the libraries in the application we run the commands:

```
dotnet add package Azure.Identity --version 1.10.4
dotnet add package Azure.Storage.Blobs --version 12.19.1
```

After loading the libraries we run the command:

```
dotnet restore
```

And we check in the **csproj file** . the libraries were loaded in the application 

### 6. Input the source code in the program.cs file

```csharp
using Azure.Storage.Blobs;
using Azure.Storage.Blobs.Models;
using Azure.Identity;

// TODO: Replace <storage-account-name> with your actual storage account name
string storageAccountName = "mynewstorageaccount1974";
var blobServiceClient = new BlobServiceClient(
        new Uri("https://" + storageAccountName + ".blob.core.windows.net"),
        new DefaultAzureCredential());

//Create a unique name for the container
string containerName = "quickstartblobs" + Guid.NewGuid().ToString();

// Create the container and return a container client object
BlobContainerClient containerClient = await blobServiceClient.CreateBlobContainerAsync(containerName);

// Create a local file in the ./data/ directory for uploading and downloading
string localPath = "data";
Directory.CreateDirectory(localPath);
string fileName = "quickstart" + Guid.NewGuid().ToString() + ".txt";
string localFilePath = Path.Combine(localPath, fileName);

// Write text to the file
await File.WriteAllTextAsync(localFilePath, "Hello, World!");

// Get a reference to a blob
BlobClient blobClient = containerClient.GetBlobClient(fileName);

Console.WriteLine("Uploading to Blob storage as blob:\n\t {0}\n", blobClient.Uri);

// Upload data from the local file
await blobClient.UploadAsync(localFilePath, true);

Console.WriteLine("Listing blobs...");

// List all blobs in the container
await foreach (BlobItem blobItem in containerClient.GetBlobsAsync())
{
    Console.WriteLine("\t" + blobItem.Name);
}

// Download the blob to a local file
// Append the string "DOWNLOADED" before the .txt extension 
// so you can compare the files in the data directory
string downloadFilePath = localFilePath.Replace(".txt", "DOWNLOADED.txt");

Console.WriteLine("\nDownloading blob to\n\t{0}\n", downloadFilePath);

// Download the blob's contents and save it to a file
await blobClient.DownloadToAsync(downloadFilePath);

// Clean up
Console.Write("Press any key to begin clean up");
Console.ReadLine();

Console.WriteLine("Deleting blob container...");
await containerClient.DeleteAsync();

Console.WriteLine("Deleting the local source and downloaded files...");
File.Delete(localFilePath);
File.Delete(downloadFilePath);

Console.WriteLine("Done");
```

### 7. Build and run the application

Type the command:

```
dotnet run
```

![image](https://github.com/luiscoco/Azure_SDK_Sample8_Create_Blob_Upload_Donwload_File/assets/32194879/cdbdd37e-518f-490b-9d0c-e080a53cf848)

![image](https://github.com/luiscoco/Azure_SDK_Sample8_Create_Blob_Upload_Donwload_File/assets/32194879/9d206959-c241-4c59-a615-56057bf611d1)

![image](https://github.com/luiscoco/Azure_SDK_Sample8_Create_Blob_Upload_Donwload_File/assets/32194879/ca0b4e85-1acf-4a5d-adaa-842e9c057f59)

![image](https://github.com/luiscoco/Azure_SDK_Sample8_Create_Blob_Upload_Donwload_File/assets/32194879/11a8bcbc-e3fb-407e-a574-e1f71dc766ab)

