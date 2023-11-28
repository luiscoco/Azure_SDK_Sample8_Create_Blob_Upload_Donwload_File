# Azure SDK Sample8 Create Blob Upload Donwload File

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

### 5. Load the Azure SDK for .NET libraries: **https://www.nuget.org/packages**

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

### Sixth step, input the source code in the program.cs file. 


### Seventh step, build and run the application

Type the command:

```
dotnet run
```

![image](https://github.com/luiscoco/Azure_SDK_Sample8_Create_Blob_Upload_Donwload_File/assets/32194879/dc198413-5427-40a4-86df-d44ed5a25729)
 

## 3. 
