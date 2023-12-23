## Architecture Diagram

![ECS](https://github.com/harsh-viradia/video-compressor/assets/140060556/a1c6048d-e438-4c47-b9ec-6a6e89f1f214)



## S3 Bucket

- Static react site hosted on S3 bucket which is pushing video on S3 queue.

## SQS Queue

- Created one standard queue.

## Lambda Function

- Launch one lambda function which has SQS Poll access and ECS full access.
- This lambda function will collect message(videos) form SQS queue and launch ECS task to compress video.
- When configure SQS queue with lambda function mention batch size and batch window, so based on that lambda function will not trigger for each message(video) of the queue so cost will reduse in that factor.

## ECS with Fargate

- ECS will compress the video and store the orignal video on S3 bucket and compressed video on other bucket.

## S3 Bucket

You can access video from compressed video bucket.