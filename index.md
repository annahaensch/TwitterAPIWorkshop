# The Twitter API

### Getting Twitter API Credentials

Before you can access the Twitter API you'll need to have a Twitter developer account.  You can apply for access as an academic researcher at the [Twitter Developer Portal](https://developer.twitter.com/en/solutions/academic-research/products-for-researchers).  This process usually take several days.

Once you've been granted access, you can login to your [Developer Dashboard](https://developer.twitter.com/en/portal/dashboard) to your retrieve your access tokens. 

![tokens.jpg](assets/img/tokens.jpg)

Be sure to copy down your keys and tokens into text file where you can find them later. 

### Python API Access with Tweepy

Tweepy is a Python library for accessing the Twitter API.  You can install Tweepy by following this [installation guide](https://docs.tweepy.org/en/latest/install.html).  Once Tweepy is installed, we will use it to connect to the Twitter API.  Replacing the values below with your own keys and tokens, you can connect to the API by executing the following in a Jupyter notebook:

```
import tweepy 

auth = tweepy.OAuthHandler(CONSUMER_KEY, SECRET_KEY)
auth.set_access_token(ACCESS_TOKEN, ACCESS_TOKEN_SECRET)
api = tweepy.API(auth, wait_on_rate_limit=True, 
        wait_on_rate_limit_notify=True)

api.verify_credentials()
```
By setting `wait_on_rate_limit` to `True`, any time the API rate limit is reached, your program will automatically pause until the rate limit resets.  

To check that you are connected to the API, you can try a query, like `api.get_user()` to see that it returns what you expect:

```
user = api.get_user("extremefriday")
user.screen_name == "extremefriday"
```
To see the full capabilities of Tweepy, you can read the [documentation](https://docs.tweepy.org/en/latest/index.html).  

### Command Line API Access with twarc

You can also access the Twitter API through the command line using [twarc](https://github.com/DocNow/twarc).  You can install twarc by following this [installation guide](https://twarc-project.readthedocs.io/en/latest/).  
