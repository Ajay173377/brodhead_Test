{
  "Version": "8.3.1.4498",
  "UId": "59c4b4bb-0e84-4744-9f6b-e442efc23c1e",
  "ManagerName": "ClientUnitSchemaManager",
  "Name": "ImplFrameComponent",
  "Caption": "Frame component",
  "ExtendParent": false,
  "DenyExtending": false,
  "Description": "",
  "Less": " ",
  "Js": "// jshint esversion: 11\r
\ndefine(\"ImplFrameComponent\", [\"@creatio-devkit/common\"], function (sdk) {\r
\n    class ImplFrameComponent extends HTMLElement {\r
\n        constructor() {\r
\n            super();\r
\n            this._dom = this.attachShadow({ mode: 'open' });\r
\n        }\r
\n\r
\n        get frameConfig() {\r
\n            return this._frameConfig || {};\r
\n        }\r
\n\r
\n        set frameConfig(value) {\r
\n            this._frameConfig = value || {};\r
\n            \r
\n            // Set default values if not provided\r
\n            this._frameConfig.src = this._frameConfig.src || \"about:blank\";\r
\n            this._frameConfig.height = this._frameConfig.height || \"94%\";\r
\n            this._frameConfig.width = this._frameConfig.width || \"100%\";\r
\n            this._frameConfig.position = this._frameConfig.position || \"absolute\";\r
\n            \r
\n            // Construct style string properly\r
\n            this._frameConfig.style = `${this._frameConfig.style || \"\"} height: ${this._frameConfig.height}; width: ${this._frameConfig.width}; position: ${this._frameConfig.position};`;\r
\n            \r
\n            if (!this._frameConfig.border) {\r
\n                this._frameConfig.style += \"border:none;\";\r
\n            }\r
\n            \r
\n            if (!this._frameConfig.sandbox) {\r
\n                this._frameConfig.sandbox = \"allow-scripts allow-forms allow-same-origin allow-downloads\";\r
\n            }\r
\n            \r
\n            this._loadFrame();\r
\n        }\r
\n\r
\n        get src() {\r
\n            return this._frameConfig?.src || \"about:blank\";\r
\n        }\r
\n\r
\n        set src(value) {\r
\n            this.frameConfig = { src: value };\r
\n        }\r
\n\r
\n        async _loadFrame() {\r
\n            this._dom.innerHTML = \"\";\r
\n\r
\n          // Show the loading mask\r
\n          var maskId = Terrasoft.Mask.show({\r
\n            caption: \"Loading...\",\r
\n            selector: \"#TabPanel\", // Apply mask to a specific container if required\r
\n          });\r
\n\r
\n            \r
\n            const iframe = document.createElement(\"iframe\");\r
\n            iframe.src = this._frameConfig.src;\r
\n            iframe.style.cssText = this._frameConfig.style;\r
\n            iframe.sandbox = this._frameConfig.sandbox;\r
\n            iframe.allowFullscreen = true;\r
\n            iframe.loading = \"lazy\";\r
\n            iframe.referrerPolicy = \"no-referrer-when-downgrade\";\r
\n\r
\n          let isMaskHidden = false;\r
\n\r
\n          // Hide loader when iframe is fully loaded\r
\n          iframe.onload = () => {\r
\n              if (!isMaskHidden) {\r
\n                  Terrasoft.Mask.hide(maskId);\r
\n                  isMaskHidden = true;\r
\n              }\r
\n          };\r
\n      \r
\n          // Fallback: hide loader after 5 seconds\r
\n          setTimeout(() => {\r
\n              if (!isMaskHidden) {\r
\n                  Terrasoft.Mask.hide(maskId);\r
\n                  isMaskHidden = true;\r
\n              }\r
\n          }, 10000);\r
\n          this._dom.appendChild(iframe);\r
\n        }\r
\n    } \r
\n    customElements.define(\"impl-frame-component\", ImplFrameComponent);\r
\n    \r
\n    sdk.registerViewElement({\r
\n        type: \"impl.FrameComponent\",\r
\n        selector: \"impl-frame-component\",\r
\n        inputs: {\r
\n            frameConfig: {},\r
\n            src: {}\r
\n        }\r
\n    });\r
\n    \r
\n    return ImplFrameComponent;\r
\n});\r
\n",
  "MetaData": "{\r
\n  \"MetaData\": {\r
\n    \"Schema\": {\r
\n      \"ManagerName\": \"ClientUnitSchemaManager\",\r
\n      \"UId\": \"59c4b4bb-0e84-4744-9f6b-e442efc23c1e\",\r
\n      \"A2\": \"ImplFrameComponent\",\r
\n      \"A5\": \"a3975f05-0d45-4efe-b04a-6979c92982f6\",\r
\n      \"B1\": [],\r
\n      \"B2\": [],\r
\n      \"B3\": [],\r
\n      \"B6\": \"957f0bcf-47ba-4aac-a833-fb65442f15a2\",\r
\n      \"B8\": \"8.1.5.2095\",\r
\n      \"HD1\": \"50e3acc0-26fc-4237-a095-849a1d534bd3\",\r
\n      \"HD4\": 1,\r
\n      \"HD6\": \"null\",\r
\n      \"HD5\": [],\r
\n      \"HD7\": [],\r
\n      \"HD8\": [],\r
\n      \"HD11\": []\r
\n    }\r
\n  }\r
\n}",
  "LocalizableValues": [
    {
      "Culture": "th-TH",
      "ResourceType": "String",
      "Key": "Caption",
      "Value": "Frame Component",
      "ImageData": ""
    },
    {
      "Culture": "hu-HU",
      "ResourceType": "String",
      "Key": "Caption",
      "Value": "Frame component",
      "ImageData": ""
    },
    {
      "Culture": "ru-RU",
      "ResourceType": "String",
      "Key": "Caption",
      "Value": "Frame Component",
      "ImageData": ""
    },
    {
      "Culture": "zh-TW",
      "ResourceType": "String",
      "Key": "Caption",
      "Value": "Frame component",
      "ImageData": ""
    },
    {
      "Culture": "it-IT",
      "ResourceType": "String",
      "Key": "Caption",
      "Value": "Frame Component",
      "ImageData": ""
    },
    {
      "Culture": "ja-JP",
      "ResourceType": "String",
      "Key": "Caption",
      "Value": "Frame Component",
      "ImageData": ""
    },
    {
      "Culture": "sq-AL",
      "ResourceType": "String",
      "Key": "Caption",
      "Value": "Frame Component",
      "ImageData": ""
    },
    {
      "Culture": "pt-BR",
      "ResourceType": "String",
      "Key": "Caption",
      "Value": "Frame Component",
      "ImageData": ""
    },
    {
      "Culture": "sv-SE",
      "ResourceType": "String",
      "Key": "Caption",
      "Value": "Frame Component",
      "ImageData": ""
    },
    {
      "Culture": "pt-PT",
      "ResourceType": "String",
      "Key": "Caption",
      "Value": "Frame Component",
      "ImageData": ""
    },
    {
      "Culture": "id-ID",
      "ResourceType": "String",
      "Key": "Caption",
      "Value": "Frame component",
      "ImageData": ""
    },
    {
      "Culture": "es-ES",
      "ResourceType": "String",
      "Key": "Caption",
      "Value": "Frame Component",
      "ImageData": ""
    },
    {
      "Culture": "pl-PL",
      "ResourceType": "String",
      "Key": "Caption",
      "Value": "Frame Component",
      "ImageData": ""
    },
    {
      "Culture": "hr-HR",
      "ResourceType": "String",
      "Key": "Caption",
      "Value": "Frame component",
      "ImageData": ""
    },
    {
      "Culture": "tr-TR",
      "ResourceType": "String",
      "Key": "Caption",
      "Value": "Frame component",
      "ImageData": ""
    },
    {
      "Culture": "ro-RO",
      "ResourceType": "String",
      "Key": "Caption",
      "Value": "Frame Component",
      "ImageData": ""
    },
    {
      "Culture": "lv-LV",
      "ResourceType": "String",
      "Key": "Caption",
      "Value": "Frame component",
      "ImageData": ""
    },
    {
      "Culture": "en-US",
      "ResourceType": "String",
      "Key": "Caption",
      "Value": "Frame component",
      "ImageData": ""
    },
    {
      "Culture": "he-IL",
      "ResourceType": "String",
      "Key": "Caption",
      "Value": "Frame Component",
      "ImageData": ""
    },
    {
      "Culture": "nl-NL",
      "ResourceType": "String",
      "Key": "Caption",
      "Value": "Frame Component",
      "ImageData": ""
    },
    {
      "Culture": "bg-BG",
      "ResourceType": "String",
      "Key": "Caption",
      "Value": "Frame component",
      "ImageData": ""
    },
    {
      "Culture": "ko-KR",
      "ResourceType": "String",
      "Key": "Caption",
      "Value": "Frame Component",
      "ImageData": ""
    },
    {
      "Culture": "cs-CZ",
      "ResourceType": "String",
      "Key": "Caption",
      "Value": "Frame Component",
      "ImageData": ""
    },
    {
      "Culture": "de-DE",
      "ResourceType": "String",
      "Key": "Caption",
      "Value": "Frame Component",
      "ImageData": ""
    },
    {
      "Culture": "vi-VN",
      "ResourceType": "String",
      "Key": "Caption",
      "Value": "Frame Component",
      "ImageData": ""
    },
    {
      "Culture": "ar-SA",
      "ResourceType": "String",
      "Key": "Caption",
      "Value": "Frame Component",
      "ImageData": ""
    },
    {
      "Culture": "fr-FR",
      "ResourceType": "String",
      "Key": "Caption",
      "Value": "Frame Component",
      "ImageData": ""
    },
    {
      "Culture": "uk-UA",
      "ResourceType": "String",
      "Key": "Caption",
      "Value": "Frame Component",
      "ImageData": ""
    }
  ],
  "Properties": [
    {
      "Name": "CreatedInVersion",
      "Value": "8.1.5.2095"
    },
    {
      "Name": "Group",
      "Value": ""
    },
    {
      "Name": "SchemaType",
      "Value": "Module"
    }
  ]
}