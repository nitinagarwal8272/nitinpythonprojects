# Twitter Sentiment Analysis

A Python application that performs sentiment analysis on Twitter tweets using the Twitter API and TextBlob library. This tool fetches tweets based on a search query and classifies them as positive, negative, or neutral.

## Features

- **Real-time Tweet Fetching**: Retrieves tweets using Twitter API v1.1
- **Sentiment Analysis**: Classifies tweets using TextBlob's sentiment analysis
- **Text Cleaning**: Removes URLs, mentions, and special characters from tweets
- **Statistical Analysis**: Provides percentage breakdown of sentiment categories
- **Rate Limit Handling**: Built-in rate limit management for API calls
- **Duplicate Prevention**: Avoids duplicate tweets in results

## Prerequisites

Before running this application, you need:

1. **Twitter Developer Account**: Apply at [developer.twitter.com](https://developer.twitter.com)
2. **Twitter API Keys**: Consumer Key, Consumer Secret, Access Token, and Access Token Secret
3. **Python 3.6+**: Make sure Python is installed on your system

## Installation

1. **Clone or download the project files**

2. **Install required dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

3. **Configure Twitter API credentials**:
   - Open the main Python file
   - Replace the placeholder values with your actual Twitter API credentials:
     ```python
     consumer_key = 'your_consumer_key_here'
     consumer_secret = 'your_consumer_secret_here'
     access_token = 'your_access_token_here'
     access_token_secret = 'your_access_token_secret_here'
     ```

## Usage

### Basic Usage

```python
# Run the script with default settings
python twitter_sentiment.py
```

### Customizing the Analysis

You can modify the `main()` function to:

- Change the search query (default: 'Donald Trump')
- Adjust the number of tweets to fetch (default: 200)
- Modify the display count for positive/negative tweets (default: 10 each)

```python
# Example customizations
tweets = api.get_tweets(query='Python programming', count=100)
```

### API Usage

```python
from twitter_sentiment import TwitterClient

# Create client instance
api = TwitterClient()

# Get tweets
tweets = api.get_tweets(query='machine learning', count=50)

# Process results
for tweet in tweets:
    print(f"Text: {tweet['text']}")
    print(f"Sentiment: {tweet['sentiment']}")
```

## Output

The application provides:

1. **Sentiment Statistics**:
   - Percentage of positive tweets
   - Percentage of negative tweets
   - Percentage of neutral tweets

2. **Sample Tweets**:
   - First 10 positive tweets
   - First 10 negative tweets

### Example Output

```
Positive tweets percentage: 45.2%
Negative tweets percentage: 32.1%
Neutral tweets percentage: 22.7%

Positive tweets:
- Great news about the new policy changes...
- Amazing progress in technology sector...

Negative tweets:
- Disappointed with recent developments...
- This policy change is problematic...
```

## Configuration Options

### TwitterClient Parameters

- `query`: Search term for tweets
- `count`: Number of tweets to fetch (max depends on API limits)
- `lang`: Language filter (default: "en")
- `result_type`: Type of tweets ("recent", "popular", "mixed")

### Sentiment Thresholds

The sentiment classification uses TextBlob's polarity scores:
- **Positive**: polarity > 0
- **Neutral**: polarity = 0
- **Negative**: polarity < 0

## Error Handling

The application handles common errors:

- **Authentication failures**: Invalid API credentials
- **Rate limit exceeded**: Automatic waiting and retry
- **Network issues**: Connection timeouts and API errors
- **Empty results**: No tweets found for the query

## Limitations

1. **API Rate Limits**: Twitter API has rate limits (300 requests per 15-minute window for search)
2. **Tweet Volume**: Limited by Twitter's search API capabilities
3. **Language Support**: Best results with English tweets
4. **Real-time Data**: Only accesses recent tweets (typically last 7 days)

## Troubleshooting

### Common Issues

1. **Authentication Error**:
   - Verify your API credentials are correct
   - Ensure your Twitter app has the necessary permissions

2. **No Tweets Retrieved**:
   - Check if your search query is too specific
   - Verify your API credentials are working
   - Try a different search term

3. **Rate Limit Errors**:
   - Reduce the count parameter
   - Wait for the rate limit window to reset
   - The application handles this automatically with `wait_on_rate_limit=True`

4. **Import Errors**:
   - Ensure all required packages are installed
   - Run `pip install -r requirements.txt`

## API Reference

### TwitterClient Methods

- `__init__()`: Initialize with API credentials
- `clean_tweet(tweet)`: Clean tweet text
- `get_tweet_sentiment(tweet)`: Get sentiment classification
- `get_tweets(query, count)`: Fetch and analyze tweets

## Contributing

To contribute to this project:

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## License

This project is open source. Please respect Twitter's API terms of service and rate limits.

## Disclaimer

This tool is for educational and research purposes. Always comply with Twitter's Developer Agreement and API Terms of Service. Be mindful of rate limits and respectful of user privacy.