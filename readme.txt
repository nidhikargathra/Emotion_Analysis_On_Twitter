*********************************** CONFIGURATION ***********************************

== API Accounts ==

For a  user to use the GeoTwitter application, a user must have registered an account to user the Twitter API and the Google Geocoding API.  Registering with these services will provide the user with the authenticat keys and tokens required to make the API calls in the GeoTwitter code.  


Information pertaining to the PythonTwitter API can be found here: 

\href{https://developer.twitter.com/en/docs/ads/general/guides/getting-started}{Getting Started with the PythonTwitter API}.  


Similarly, the information for Google's geocoding API can be found here: 

\href{https://developers.google.com/maps/documentation/geocoding/start}{Get Started with the Geocoding API}.
 

== Authentication File ==

Once accounts are setup with the two API services, the keys and tokens will need to be stored in JSON format in a file called OAuth_Keys.json.  This file should be placed in the same directory as the GeoTwitter Jupyter Notebook.  Alternatively, the parameter CREDFILE in the code can be changed to reference a different location and filename for the JSON credential file.  A sample file containing dummy keys currently exists in the GeoTwitter zip file.

The file must contain the following key value pairs all at the initial level in the JSON file.

    KEY         VALUE
    Token       Twitter API token
    SToken      Twitter API secret token
    Key         Twitter API key
    SKey        Twitter API secret key
    GoogleKey   Google MAP API Key
	
== Data Subdirectory ==

Lastly, the data subdirectory must be included with the Jupyter Notebook.  This folder, included in the submission, contains data for the nationally sampled sentiment in JSON format.  The file is called sentiment_sample.json.

******************************** Running the Code ********************************

After all of the configuration steps have been completed, the Juypiter Notebook is ready to be run.  In order to start the GeoTwitter Application, all modules in the Jupyter Notebook must be run in order.  The final module starts the Bokeh application and will then be used to interact with the application.

IMPORTANT: Make sure that the port number in the final line of code shown below matches the port number of the Jupyter Notebook URL in the browser it is executing in.

    show(app, notebook\_url="localhost:\textbf{8888}", notebook\_handle=True)

Once the application is running, the user can supply input using the menu on the left and then submit their query by clicking on the "Get Tweets" or "Apply Filter" button.

*********************************** Limitations ***********************************

== Bokeh Server ==

Due to limitations with Bokeh Server, the same geographic location cannot be searched multiple times without restarting the Jupyter Kernel.  This is a result of the Bokeh's functionality to load specific tiles from a geographic tile provider.  Multiple searches can be done but different locations must be used.


== Python Twitter API ==

The PythonTwitter API is limited according to the rate limits specified on the Twitter API website.  As of the writing of this document the limit for retrieving tweets is 450 requests per 15-minute window.  Given that the GeoTwitter application will issue up to 50 batched requests to the Twitter API for a given search the application is theoretically limited to 9 searches every 15 minutes.  If the limit is hit, the application will return empty results in the format below.

== Google Geocoding API ==

The Google geocoding API is also rate-limited but given that the GeoTwitter application only issues one API request for each search, the user is much more likely to be constrained by the limits of the Twitter API.  A user would have to submit 2500 requests in a given 24-hour period to hit Google's rate limit.