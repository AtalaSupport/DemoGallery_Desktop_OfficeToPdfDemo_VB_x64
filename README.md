# Office to PDF Demo
A very simple console app that converts an Office (DOC, DOCX, RTF, PPT, PPTX, XLS, XLSX file into a PDF by using in a memory-efficient ay using FileSystemImageSource.

Who says you always need a viewer in an imaging application?

This console app uses our FileSystemImageSource to read each frame of the target file directly into a PDF Encoder. Each page read will trigger a Compression Selector event so you can choose the best compression to use for that specific page's Pixel Format.  

This approach can easily be adapted to services or plumbed in to batch-based processing.  

By setting a handler for PdfEnc.SetEncoderCompression, we are able to dynamically select the most appropriate form of image compression to apply, based on the PixelFormat (color depth) of each page.  

NOTE that tecnically, the input file is not limited to Offic, any supported input file type may be used (Png, BMP, Jpeg, etc..). Some require additional references and to have additional decoders added to RegisteredDecoders.Decoders. Please feel free to reach out to support if you have questions.  

This is the VB.NET version. There is a [C# version](https://github.com/AtalaSupport/DemoGallery_Desktop_OfficeToPdfDemo_CS_x64)  available.

## Instructions
After installing and activating the SDK, you can unzip, build and run this solution. It will prompt you for an Office File with an OpenFileDialog.

Select the PDF you want to convert and open. It will then prompt you where to save the TIFF and for filename. The file will be converted and saved.

## Licensing
This demo assumes you have a license for DotImage Document Imaging and OfficeDecoder add-on (or you can request a 30 day evaluation when installing/activating)  


## SDK Dependencies
This app was built based on 2026.2.0.0. It targets .NET Framework 4.6.2 and was created in Visual Studio 2022. You must have our SDK installed (and licesed per above)

[Download DotImage](https://www.atalasoft.com/BeginDownload/DotImageDownloadPage)

### OfficeDecoder Additional Dependencies
The OfficeDecoder has dependencies on PerceptiveFilters. These can not be referenced as otehr dlls and thus must be copied into the bin directory. In this demo we have hard copied the required dlls in as part of the project and set their build action to Copy if Newer.

The files can be found when installing the SDK in: `C:\Program Files (x86)\Atalasoft\DotImage 2026.2\bin\PerceptiveDocumentFilters\intel-64`

- ISYS11df.dll
- ISYSreaders.dll
- ISYSreadershd.dll
- Perceptive.DocumentFilters.dll

- For NuGet, see below


### Using NuGet for SDK Dependencies
We do publish our SDK components to NuGet. We have chosen to base the demo on local installed SDK because this leads to much smaller applications (NuGet packages add a lot of overhead due to the way they're packaged and deployed, and many of our demos -- including this one -- are often used to reproduce issues that need to be submitted to support. Apps that use NuGet are often significantly larger and run up against our maximum support case upload size)

Still, if you wish to use NuGet for the dependencies instead of relying on locally installed SDK, you can.

- Take note of each of the references we've included:
    - Atalasoft.DotImage.dll
    - Atalasoft.DotImage.AdvancedDocClean.dll
    - Atalasoft.DotImage.Lib.dll
    - Atalasoft.DotImage.Office.dll
    - Atalasoft.DotImage.Pdf.dll
    - Atalasoft.DotImage.PdfDoc.Bridge.dll
    - Atalasoft.DotImage.PdfReader.dll
    - Atalasoft.PdfDoc.dll
    - Atalasoft.Shared.dll
- Remove those referneces
- Open the NuGet Package Manger from `Tools -> NuGet Package Manager -> Manage NuGet Packages for this Solution`
- Browse for and install  Atalasoft.DotImage.x64 - It will pull in DotImage Document Imaging (the base SDK) and shared dll
- Browse for and install Atalasoft.Office.x64 - Required to bring in the base OCR and Tesseract dependencies
- Browse for and install Atalasoft.Pdf.x64 - Required to bring in PdfEncoder


## Downloading source
The sources can be downloaded for [c#](https://github.com/AtalaSupport/DemoGallery_Desktop_OfficeToPdfDemo_CS_x64/archive/refs/heads/main.zip) and [VB.NET](https://github.com/AtalaSupport/DemoGallery_Desktop_OfficeToPdfDemo_VB_x64/archive/refs/heads/main.zip)


## Cloning
We recommend the following if you wish to donload/clone a copy

Example: git for windows
```bash
git clone https://github.com/AtalaSupport/DemoGallery_Desktop_OfficeToPdfDemo_CS_x64.git OfficeToPdfDemo
```


## Related documentation
In addition to this README, the Atalasoft documentation set includes the following:  
- [AtalaSupport Github](https://github.com/AtalaSupport/) For an extensive set of sample apps.  
- [Atalasoft's APIs & Developer Guides page](https://www.atalasoft.com/Support/APIs-Dev-Guides) for our Developers guide and API references.  
- [Atalasoft Support](http://www.atalasoft.com/support/) for our main support portal.
- [Atalasoft Knowledgebase](http://www.atalasoft.com/kb2) where you can find answers to common questions / issues.  


## Getting Help for Atalasoft products
Atalasoft regularly updates our support [Knowledgebase](http://www.atalasoft.com/kb2) with the latest information about our products. To access some resources, you must have a valid Support Agreement with an authorized Atalasoft Reseller/Partner or with Atalasoft directly. Use the tools that Atalasoft provides for researching and identifying issues. 

Customers with an active evaluation, or those with active support / maintenance may [create a support case](https://www.atalasoft.com/Support/my-portal/Cases/Create-Case) 24/7, or call in to support ([+1 949 236-6510](tel:19492366510) ) during our normal support hours (Monday - Friday 8:00am to 5:00PM Eastern (New York) time).  

Customers who are unable to create a case or call in may [email our Sales Team](email:sales@atalasoft.com).  


