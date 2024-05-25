# Google Indexing API
**I'm glad you found this repository. If you find the tool useful, you can buy me a coffee on Buy Me A Coffee :)**

<a href="https://www.buymeacoffee.com/marekfoltas" target="_blank"><img src="https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png" alt="Buy Me A Coffee" style="height: 41px !important;width: 174px !important;box-shadow: 0px 3px 2px 0px rgba(190, 190, 190, 0.5) !important;-webkit-box-shadow: 0px 3px 2px 0px rgba(190, 190, 190, 0.5) !important;" ></a>

This tool allows you to submit a bulk number of URLs for indexing using the Indexing API. If you don't know what the Indexing API is, you can find more information [here](https://developers.google.com/search/apis/indexing-api/v3/quickstart).

Why should you use it and why is it better than submitting URLs via Google Search Console?



* you can submit up to 200 URLs per day
* you can submit up to 100 URLs at once
* URLs submitted this way appear in the index much faster than with conventional methods

This is what Google says about it:

> We recommend using the Indexing API instead of sitemaps because it allows Googlebot to index pages faster than updating the sitemap and > signaling that fact to Google systems.

I use this on various sites (new, old) and every time the indexing is instant. Usually, all URLs (e.g., 200 new subpages) appear in the index within 24h after submitting the indexing request.

![indexing api](https://bootcampy.pl/wp-content/uploads/2022/03/18.png "Graph with indexed URLs")

![indexing api](https://bootcampy.pl/wp-content/uploads/2022/03/19.png "Graph with indexed URLs")

## Alright, but how do I run it?

### Create a service account in Google Cloud Platform

To use the Indexing API, you first need to create a service account in Google Cloud Platform:

* Go to [https://console.developers.google.com/iam-admin/serviceaccounts](https://console.developers.google.com/iam-admin/serviceaccounts)

* Click **CREATE PROJECT**

  ![create project](https://bootcampy.pl/wp-content/uploads/2022/03/1.png "Create project")

* Enter the name of your project and click **CREATE**

  ![create](https://bootcampy.pl/wp-content/uploads/2022/03/2.png "Create")

* Click **CREATE SERVICE ACCOUNT**

  ![create service account](https://bootcampy.pl/wp-content/uploads/2022/03/3.png "Create service account")

* Enter the account name, the rest can be skipped

  ![account name](https://bootcampy.pl/wp-content/uploads/2022/03/4.png "Enter account name")

* Save the name (E-mail) of the service account, as you will need to add it to GSC

* Next to your service account, click the three dots and **Manage keys**

  ![manage keys](https://bootcampy.pl/wp-content/uploads/2022/03/5.png "Manage keys")

* Create a new key

  ![create new key](https://bootcampy.pl/wp-content/uploads/2022/03/6.png "Create new key")

* JSON key type

  ![JSON key type](https://bootcampy.pl/wp-content/uploads/2022/03/7.png "JSON key type")

* The key should be saved to your disk (JSON file)

  ![download key to disk](https://bootcampy.pl/wp-content/uploads/2022/03/8.png "Download key to disk")


The downloaded key file will be used later; it is necessary for the tool to work correctly.


### Add the Indexing API to the project

* Go to the API library

  ![API library](https://bootcampy.pl/wp-content/uploads/2022/03/9.png "API library")

* Type “indexing api” in the search bar

  ![search bar](https://bootcampy.pl/wp-content/uploads/2022/03/10.png "Type indexing API in the search bar")

* select Indexing API from the list

  ![Indexing API](https://bootcampy.pl/wp-content/uploads/2022/03/11.png "Indexing API")

* enable the API

  ![Enable API](https://bootcampy.pl/wp-content/uploads/2022/03/12.png "Enable API")


### Add the service account to GSC

Once you have created the service account, add it as an **owner** to Google Search Console:

* log in to the Webmaster Central - [link](https://www.google.com/webmasters/verification/home)
* select the property to which you want to add the account
* add the previously created service account

  ![gsc](https://bootcampy.pl/wp-content/uploads/2022/03/13.png "Add service account to GSC")

### Run the tool

To run the tool, you will need Node.js and npm installed, which you can download [here](https://nodejs.org/en/).

Once you have that set up, download the repository. There is a file named service_account.json in the folder, which is just a placeholder. Delete it and replace it with the previously downloaded JSON key file. Rename the file to service_account.json.

Open the project, e.g., in Visual Studio Code ([link](https://code.visualstudio.com/)) and in the terminal, type:


![npm install](https://bootcampy.pl/wp-content/uploads/2022/03/16.png "npm install")

Once the installation is complete, type in the terminal:


![npm install](https://bootcampy.pl/wp-content/uploads/2022/03/17.png "npm install")

This will run the tool, and it will be available at [http://localhost:8000/](http://localhost:8000/)

In the form, paste the URLs you want to submit for indexing.

![form](https://bootcampy.pl/wp-content/uploads/2022/03/14.png "Form")

If you did everything correctly, you should get a 200 response after submitting the form. For a larger number of URLs, it's more convenient to check this in the browser console.

![response](https://bootcampy.pl/wp-content/uploads/2022/03/15.png "Response")
