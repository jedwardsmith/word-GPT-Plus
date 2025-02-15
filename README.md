<div align="center">
  <a href="https://github.com/Kuingsmile/word-GPT-Plus">
    <img src="https://user-images.githubusercontent.com/96409857/233920113-b6919e19-484e-4a4b-82ff-5c72f7314025.png" alt="Logo" height="100">
  </a>
  <br />
  <h3 align="center">Word & chatGPT</h3>
</div>

English | [简体中文](https://github.com/Kuingsmile/word-GPT-Plus/blob/master/README_cn.md)

## Introduction
Word GPT Plus is a word add-in which integrates the chatGPT model into Microsoft Word. It allows you to generate text based on the text you have written in your document. You can use it to translate, summarize, polish or even write a whole document from scratch.

## Features
- Built-in prompts for translation, summarization, polishing, and academic writing
- Multiple platforms supported
  -- OpenAI API (and other models compatible with OpenAI, such as DeepSeek)
  -- Azure OpenAI API
  -- Ollama2
-- Google Gemini Pro API
  -- Groq
- Support for multiple languages
- Custom prompts can be set and saved for future use
- Ability for users to set temperature and max tokens
- Proxy support

![230424 091554](https://user-images.githubusercontent.com/96409857/233878627-6b5abdfd-7ff6-4818-8b26-d78f74ea0e85.gif)
![230424 091221](https://user-images.githubusercontent.com/96409857/233878368-3a793d8b-3740-4471-822b-0e062415b704.gif)

## Requirements
### Software
- Microsoft Word 2016/2019 retail version, Microsoft Word 2021 or Microsoft 365
- Edge WebView2 Runtime [https://developer.microsoft.com/en-us/microsoft-edge/webview2/](https://developer.microsoft.com/en-us/microsoft-edge/webview2/)
- if you use self-hosted service, you need Node.js 18+
**Note:** Office add-in can only be used with docx files, it does not support doc files.

### Account
API Keys are required.  Request key from the relevant service.
#### OpenAI API Key
Official API requires an OpenAI api key. Requst key from [https://platform.openai.com/account/api-keys](https://platform.openai.com/account/api-keys)
#### Azure OpenID API
You need to register first,  go to [Azure OpenAI API application website](https://go.microsoft.com/fwlink/?linkid=2222006&clcid=0x409&culture=en-us&country=us) to register for the Azure OpenAI Service.
#### Google Gemini API Key
You need to go to [Google AI](https://developers.generativeai.google/) to apply for qualification for Google Gemini Pro API. The free version is currently limited to 60 requests per minute.
#### Groq API Key
Groq's api key can be requested at [https://console.groq.com/keys](https://console.groq.com/keys).

## Getting Started
There are two ways to install Word GPT Plus: through my free hosting service, or by self-hosting it.

I recommend utilizing my hosting service as it is both user-friendly and does not require installation of additional dependencies. Furthermore, you will have access to the most up-to-date version of Word GPT Plus at all times.

Rest assured that your privacy is protected as all data is saved using localStorage.

However, if you desire faster speeds and possess expertise with Node.js, self-hosting is also an option.

### Hosted Service
There is a hosted isntance provided by kuingsmile.
#### localhost
This service is built using Cloudflare Pages.  The domain name is: [https://word.msq.pub](https://word.msq.pub)

**Note: Users in China** You may experience conenctivity issues, please verify connection by using `ping word.msq.pub` to see if you can access the domain.

**You can add `msq.pub` to your proxy software's rules, or use self-hosted.**

1. Download the add-in `manifest.xml` file and Save it to a directory on your computer, such as `C:\Users\username\Documents\WordGPT`.
    -- download link: [manifest.xml](https://github.com/Kuingsmile/word-GPT-Plus/blob/master/release/instant-use/manifest.xml)
2. Follow the [Sideload add-in](#sideload-add-in) instructions below to install the add-in.
#### Docker
You can also use Docker to run the service, first `docker pull` the image, then run the container.
```bash
docker pull kuingsmile/word-gpt-plus
docker run -d -p 3000:80 kuingsmile/word-gpt-plus
````
Modify `[localhost:3000](http://localhost:3000)` in manifest.xml to reflect your server address.

Install using the [Sideload add-in](#sideload-add-in) instructions below.

### Self-hosted

If you want to host the add-in, first clone the repo and install dependencies, then run the project. Note: Requires Node.js 16+
````bash
git clone https://github.com/Kuingsmile/Word-GPT-Plus.git
yarn
yarn run serve
````
Settings, Metadata, and Permissions are in the 
[manifest.xml](https://github.com/Kuingsmile/word-GPT-Plus/blob/master/release/self-hosted/manifest.xml) file.

Follow [Sideload add-in](#sideload-add-in) instructions below to install the add-in.
### Sideload add-in
To get started with Word GPT Plus, you will need to sideload the add-in into Microsoft Word.

You can find instructions provided by Microsoft at the following link: [sideload office add-ins](https://learn.microsoft.com/en-us/office/dev/add-ins/testing/create-a-network-shared-folder-catalog-for-task-pane-and-content-add-ins)

1. Go to the folder where you saved the `manifest.xml` file, for example `C:\Users\username\Documents\WordGPT`.
2. Share folder to yourself and provision users.
    -- Open the context menu for the folder (right-click the folder) and select **Properties**.
    -- Within the **Properties** dialog box, select the **Sharing** tab, and then select **Share**.

    ![image](https://learn.microsoft.com/en-us/office/dev/add-ins/images/sideload-windows-properties-dialog.png)

    -- Within the **Network access** dialog box, add yourself and grant users access rights to Word GPT Plus by adding them here. Choose the **Share** button.  A confirmation will be displayed when folder is shared.
    -- Note **full network path** that's displayed immediately following the folder name.

    ![image](https://learn.microsoft.com/en-us/office/dev/add-ins/images/sideload-windows-network-access-dialog.png)
4. Open a new document in Word, choose the **File** tab, and then choose **Options**.
5. Choose **Trust Center**, and then choose the **Trust Center Settings** button.
6. Choose **Trusted Add-in Catalogs**.
7. In the **Catalog Url** box, enter the **full network path** and then choose **Add Catalog**.
8. Select the **Show in Menu** check box, and then choose **OK**.
    ![image](https://learn.microsoft.com/en-us/office/dev/add-ins/images/sideload-windows-trust-center-dialog.png)
9. Close and then restart Word.
10. Click **Insert** > **My Add-ins** > **Shared Folder**, choose **GPT Plus**, and then choose **Add**.
11. Enjoy!
![image](https://user-images.githubusercontent.com/96409857/234744280-9d9f13cf-536b-4fb5-adfa-cbec262d56a2.png)

## How to enter API key

After entering Word GPT Plus, click the orange `Settings` button on the homepage to enter the settings page, where you can switch APIs and enter API keys.

## Contributing

If you have a suggestion that would make this better, please fork the repo and create a pull request.

## License

MIT License

## Show your support

Give a ⭐️ if this project helped you!
