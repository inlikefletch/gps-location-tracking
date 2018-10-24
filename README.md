# gps-location-tracking
GPS Location Tracking

The following process reviews creating an Android GPS tracking/location solution.

1) Get your GPS coordinates. Use GPS Logger for Android. Log to a custom URL, i.e. https://s3.us-west-2.amazonaws.com/my-s3-bucket/index.html?lat=%LAT&longitude=%LON&time=%TIME&s=%SPD. Set logging interval and app to start on bootup.

2) Create the above s3 object my-s3-bucket/index.html

3) Enable object level logging on the s3 bucket, also known as CloudTrail

4) Create a Lambda function that does the following:
- Get and read the contents of those CloudTrail logs
- Parse the coordinates
- Create geojson object
- Put geojson object to S3

5) Use geojson.io to view geojson object
