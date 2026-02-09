{
  "Version": "8.3.1.4498",
  "UId": "9b2d72a3-1655-40ce-aa57-7eadd77b5502",
  "ManagerName": "SourceCodeSchemaManager",
  "Name": "ImplLicensing",
  "Caption": "ImplLicensing",
  "ExtendParent": false,
  "DenyExtending": false,
  "Description": "",
  "SourceCode": "namespace Terrasoft.Configuration.ImplLicensing\r
\n{\r
\n\tusing System;\r
\n\tusing System.ServiceModel;\r
\n\tusing System.ServiceModel.Web;\r
\n\tusing System.ServiceModel.Activation;\r
\n\tusing Terrasoft.Web.Common;\r
\n\r
\n    [ServiceContract]\r
\n    [AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Required)]\r
\n    public class ImplLicenseValidationService : BaseService\r
\n    {\r
\n        [OperationContract]\r
\n        [WebInvoke(\r
\n            Method = \"POST\",\r
\n            ResponseFormat = WebMessageFormat.Json,\r
\n            BodyStyle = WebMessageBodyStyle.Bare)]\r
\n        public ImplLicenseValidationResponse CheckLicense()\r
\n        {\r
\n\t\t\ttry\r
\n\t\t\t{\r
\n\t\t\t\tif (UserConnection.LicHelper.GetHasOperationLicense(\"ImplSmarten.Use\") ||\r
\n\t\t\t\t\tUserConnection.LicHelper.GetHasOperationLicense(\"ImplSmartenView.Use\"))\r
\n\t\t\t\t{\r
\n\t\t            return new ImplLicenseValidationResponse { Message = string.Empty };\r
\n\t\t        }\r
\n\t\t        return new ImplLicenseValidationResponse { Message = \"No License!\" };\r
\n\t\t    }\r
\n\t\t    catch (Exception ex)\r
\n\t\t    {\r
\n\t\t        // Log exception instead of returning it\r
\n\t\t        return new ImplLicenseValidationResponse { Message = \"No License!\" };\r
\n\t\t    }\r
\n        }\r
\n\r
\n\t\t\r
\n\t\t[OperationContract]\r
\n\t\t[WebInvoke(Method = \"POST\", ResponseFormat = WebMessageFormat.Json, BodyStyle = WebMessageBodyStyle.Bare)]\r
\n\t\tpublic ImplLicenseValidationResponse CheckViewLicense()\r
\n\t\t{\r
\n\t\t    try\r
\n\t\t    {\r
\n\t\t        // Allow if user has either full or viewer license\r
\n\t\t        bool hasFullLicense = UserConnection.LicHelper.GetHasOperationLicense(\"ImplSmarten.Use\");\r
\n\t\t        bool hasViewerLicense = UserConnection.LicHelper.GetHasOperationLicense(\"ImplSmartenView.Use\");\r
\n\t\t\r
\n\t\t        if (hasFullLicense || hasViewerLicense)\r
\n\t\t        {\r
\n\t\t            return new ImplLicenseValidationResponse { Message = string.Empty };\r
\n\t\t        }\r
\n\t\t\r
\n\t\t        return new ImplLicenseValidationResponse { Message = \"No License!\" };\r
\n\t\t    }\r
\n\t\t    catch (Exception ex)\r
\n\t\t    {\r
\n\t\t        // Logger.Error(ex); \r
\n\t\t        return new ImplLicenseValidationResponse { Message = \"No License!\" };\r
\n\t\t    }\r
\n\t\t}\r
\n    }\r
\n\r
\n    public class ImplLicenseValidationResponse\r
\n    {\r
\n        public string Message { get; set; }\r
\n    }\r
\n}\r
\n",
  "MetaData": "{\r
\n  \"MetaData\": {\r
\n    \"Schema\": {\r
\n      \"ManagerName\": \"SourceCodeSchemaManager\",\r
\n      \"UId\": \"9b2d72a3-1655-40ce-aa57-7eadd77b5502\",\r
\n      \"A2\": \"ImplLicensing\",\r
\n      \"A5\": \"3440e9b4-1cb9-45ae-b881-b8896df9d62a\",\r
\n      \"B1\": [],\r
\n      \"B2\": [],\r
\n      \"B3\": [],\r
\n      \"B6\": \"957f0bcf-47ba-4aac-a833-fb65442f15a2\",\r
\n      \"B8\": \"8.3.0.3017\",\r
\n      \"HD1\": \"50e3acc0-26fc-4237-a095-849a1d534bd3\"\r
\n    }\r
\n  }\r
\n}",
  "LocalizableValues": [
    {
      "Culture": "th-TH",
      "ResourceType": "String",
      "Key": "Caption",
      "Value": "ImplLicensing",
      "ImageData": ""
    },
    {
      "Culture": "hu-HU",
      "ResourceType": "String",
      "Key": "Caption",
      "Value": "ImplLicensing",
      "ImageData": ""
    },
    {
      "Culture": "ru-RU",
      "ResourceType": "String",
      "Key": "Caption",
      "Value": "ImplLicensing",
      "ImageData": ""
    },
    {
      "Culture": "zh-TW",
      "ResourceType": "String",
      "Key": "Caption",
      "Value": "ImplLicensing",
      "ImageData": ""
    },
    {
      "Culture": "it-IT",
      "ResourceType": "String",
      "Key": "Caption",
      "Value": "ImplLicensing",
      "ImageData": ""
    },
    {
      "Culture": "ja-JP",
      "ResourceType": "String",
      "Key": "Caption",
      "Value": "ImplLicensing",
      "ImageData": ""
    },
    {
      "Culture": "sq-AL",
      "ResourceType": "String",
      "Key": "Caption",
      "Value": "ImplLicensing",
      "ImageData": ""
    },
    {
      "Culture": "pt-BR",
      "ResourceType": "String",
      "Key": "Caption",
      "Value": "ImplLicensing",
      "ImageData": ""
    },
    {
      "Culture": "sv-SE",
      "ResourceType": "String",
      "Key": "Caption",
      "Value": "ImplLicensing",
      "ImageData": ""
    },
    {
      "Culture": "pt-PT",
      "ResourceType": "String",
      "Key": "Caption",
      "Value": "ImplLicensing",
      "ImageData": ""
    },
    {
      "Culture": "id-ID",
      "ResourceType": "String",
      "Key": "Caption",
      "Value": "ImplLicensing",
      "ImageData": ""
    },
    {
      "Culture": "es-ES",
      "ResourceType": "String",
      "Key": "Caption",
      "Value": "ImplLicensing",
      "ImageData": ""
    },
    {
      "Culture": "pl-PL",
      "ResourceType": "String",
      "Key": "Caption",
      "Value": "ImplLicensing",
      "ImageData": ""
    },
    {
      "Culture": "hr-HR",
      "ResourceType": "String",
      "Key": "Caption",
      "Value": "ImplLicensing",
      "ImageData": ""
    },
    {
      "Culture": "tr-TR",
      "ResourceType": "String",
      "Key": "Caption",
      "Value": "ImplLicensing",
      "ImageData": ""
    },
    {
      "Culture": "ro-RO",
      "ResourceType": "String",
      "Key": "Caption",
      "Value": "ImplLicensing",
      "ImageData": ""
    },
    {
      "Culture": "lv-LV",
      "ResourceType": "String",
      "Key": "Caption",
      "Value": "ImplLicensing",
      "ImageData": ""
    },
    {
      "Culture": "en-US",
      "ResourceType": "String",
      "Key": "Caption",
      "Value": "ImplLicensing",
      "ImageData": ""
    },
    {
      "Culture": "he-IL",
      "ResourceType": "String",
      "Key": "Caption",
      "Value": "ImplLicensing",
      "ImageData": ""
    },
    {
      "Culture": "nl-NL",
      "ResourceType": "String",
      "Key": "Caption",
      "Value": "ImplLicensing",
      "ImageData": ""
    },
    {
      "Culture": "bg-BG",
      "ResourceType": "String",
      "Key": "Caption",
      "Value": "ImplLicensing",
      "ImageData": ""
    },
    {
      "Culture": "ko-KR",
      "ResourceType": "String",
      "Key": "Caption",
      "Value": "ImplLicensing",
      "ImageData": ""
    },
    {
      "Culture": "cs-CZ",
      "ResourceType": "String",
      "Key": "Caption",
      "Value": "ImplLicensing",
      "ImageData": ""
    },
    {
      "Culture": "de-DE",
      "ResourceType": "String",
      "Key": "Caption",
      "Value": "ImplLicensing",
      "ImageData": ""
    },
    {
      "Culture": "vi-VN",
      "ResourceType": "String",
      "Key": "Caption",
      "Value": "ImplLicensing",
      "ImageData": ""
    },
    {
      "Culture": "ar-SA",
      "ResourceType": "String",
      "Key": "Caption",
      "Value": "ImplLicensing",
      "ImageData": ""
    },
    {
      "Culture": "fr-FR",
      "ResourceType": "String",
      "Key": "Caption",
      "Value": "ImplLicensing",
      "ImageData": ""
    },
    {
      "Culture": "uk-UA",
      "ResourceType": "String",
      "Key": "Caption",
      "Value": "ImplLicensing",
      "ImageData": ""
    }
  ],
  "Properties": [
    {
      "Name": "CreatedInVersion",
      "Value": "8.3.0.3017"
    }
  ]
}