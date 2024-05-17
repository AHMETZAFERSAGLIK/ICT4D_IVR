# ICT4D_IVR
To create comprehensive GitHub documentation for the VoiceXML application, we'll include the following sections: Introduction, Prerequisites, Setup, Usage, VoiceXML File Explanation, Azure Blob Storage Integration, and Updating Messages. We'll use the information provided to structure this documentation.

### VoiceXML IVR System Documentation

---

## Introduction

This repository contains the VoiceXML-based IVR system designed to share information about Artemisia cultivation and disease prevention. The system uses AI-generated voice recordings stored on Azure Blob Storage and supports multiple languages, including English, French, and Bambara. This documentation provides a step-by-step guide to set up, use, and update the IVR system.

## Prerequisites

Before setting up the IVR system, ensure you have the following:
- An Azure account with a Blob Storage container
- Access to the Azure portal
- Basic knowledge of VoiceXML
- Audio files for the IVR prompts in the required languages

## Setup

### 1. Clone the Repository

Clone this repository to your local machine using the following command:

```bash
git clone https://github.com/AHMETZAFERSAGLIK/ICT4D_IVR
```

### 2. Upload Audio Files to Azure Blob Storage

1. Navigate to the Azure portal.
2. You can access the storage account through this [storage account](https://portal.azure.com/#@vunl.onmicrosoft.com/resource/subscriptions/0f8c043b-7d9a-4be5-99e2-265b83fdd0d3/resourceGroups/vu_voice_app_rsrc/providers/Microsoft.Storage/storageAccounts/vuvoiceappstorage/containers) blob storage. Inside you will find a container named `voiceblob`.
3. Upload the AI-generated voice recordings to this container. Ensure the container is set to public access.

### 3. Update the VoiceXML File

Ensure the `vxml` file in your repository points to the correct URLs of the uploaded audio files. The current setup uses the following structure:

```<vxml version="2.1">
<script id="eppiocemhmnlbhjplcgkofciiegomcon"/>
<script/>
<script/>
<menu id="mainMenu" dtmf="true">
<prompt>
<audio src="https://vuvoiceappstorage.blob.core.windows.net/voiceblob/english_select_language.wav"/>
<audio src="https://vuvoiceappstorage.blob.core.windows.net/voiceblob/french_select_language.wav"/>
<audio src="https://vuvoiceappstorage.blob.core.windows.net/voiceblob/Bambara_select_language.wav"/>
</prompt>
<choice next="#englishMenu" dtmf="1"/>
<choice next="#frenchMenu" dtmf="2"/>
<choice next="#bambaraMenu" dtmf="3"/>
</menu>
<menu id="englishMenu" dtmf="true">
<prompt>
<audio src="https://vuvoiceappstorage.blob.core.windows.net/voiceblob/selected_English.wav"/>
</prompt>
<choice next="#cultivationForm" dtmf="1"/>
<choice next="#plantingForm" dtmf="2"/>
<choice next="#preventionForm" dtmf="3"/>
</menu>...
```



## Usage

### 1. Deploy the VoiceXML Application

1. Deploy the `vxml` file to your VoiceXML platform.
2. Ensure your IVR system is configured to use the deployed `vxml` file.

### 2. Interact with the IVR System

1. Dial into the IVR system.
2. Follow the prompts to select your preferred language.
3. Navigate through the options to receive information on Artemisia cultivation, planting instructions, and disease prevention.

## VoiceXML File Explanation

The `vxml` file defines the structure and flow of the IVR system. Here's a breakdown:

- **Main Menu**: Prompts the user to select a language.
- **Language Menus**: Provides options for different information categories in the selected language.
- **Forms**: Contains the prompts for specific information, such as cultivation, planting, and prevention.

## Azure Blob Storage Integration

The IVR system uses Azure Blob Storage to store and serve audio files. The recordings are linked directly in the `vxml` file using their URL paths. Ensure the container is set to public access to allow the IVR system to fetch the files.

### Accessing Azure Blob Storage

1. Go to your Blob Storage account on Azure.
2. Open the `voiceblob` container.
3. Upload new audio files as needed.
4. Ensure the files are publicly accessible.

## Updating Messages

To update or add new messages:

1. Create or modify the audio recordings.
2. Upload the new recordings to the `voiceblob` container on Azure.
3. Update the `vxml` file with the new URLs of the recordings.
4. Redeploy the updated `vxml` file to your VoiceXML platform.

---

This documentation provides a detailed guide for setting up and maintaining the VoiceXML IVR system. By following these steps, you can ensure that the IVR system remains up-to-date and continues to provide valuable information to its users.

---

## Diagram

The following diagram illustrates the user interaction flow within the IVR system:

![IVR System Interaction Flow](https://path-to-your-diagram.png)

## Azure Blob Storage Screenshot

The following screenshot shows the `voiceblob` container in Azure Blob Storage:

![Azure Blob Storage](https://path-to-your-screenshot.png)

---

Feel free to reach out if you have any questions or need further assistance.
