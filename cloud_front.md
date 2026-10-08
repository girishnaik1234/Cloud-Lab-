# Lab 11 — Create Video Streaming Service Using S3 and CloudFront

## Aim

To create a video streaming service using S3 and CloudFront and AWS Elemental MediaConvert Digital Rights Management System.

---

## Step 1: Set Up Amazon S3 Bucket

1. Login to the **AWS Management Console**.
2. Go to **Services → S3**.
3. Click **Create bucket**.
4. Enter a unique bucket name.

   Example:

   `my-video-streaming-bucket-2026`

5. Select the required **AWS Region**.
6. Keep **Block all public access** checked.
7. Enable **Bucket Versioning**.
8. Enable **Default Encryption** using **SSE-S3**.
9. Click **Create bucket**.

---

## Step 2: Upload a Video

1. Open the newly created S3 bucket.
2. Click **Upload**.
3. Select a test `.mp4` video.
4. Click **Upload**.
5. Check that the video is available in the bucket.

Example:

    my-video-streaming-bucket-2026/
    └── sample.mp4

---

## Step 3: Create CloudFront Distribution

1. Search for **CloudFront** in the AWS Console.
2. Open **CloudFront**.
3. Click **Create distribution**.

### Origin Settings

4. Under **Origin domain**, select the S3 bucket.
5. Under **Origin access**, select:

   `Origin access control settings (recommended)`

6. Click **Create control setting**.
7. Keep the default settings.
8. Click **Create**.

### Default Cache Behavior Settings

9. Under **Viewer protocol policy**, select:

   `Redirect HTTP to HTTPS`

10. Under **Allowed HTTP methods**, select:

   `GET, HEAD`

11. Under **Cache key and origin requests**, select:

   `Cache policy and origin request policy (recommended)`

12. Select:

   `CachingOptimized`

13. For the basic lab, select:

   `Do not enable security protections`

14. Click **Create distribution**.

---

## Step 4: Update S3 Bucket Policy

1. After creating the CloudFront distribution, click **Copy policy**.
2. Go back to **S3**.
3. Open your video bucket.
4. Click **Permissions**.
5. Scroll down to **Bucket policy**.
6. Click **Edit**.
7. Paste the copied CloudFront policy.
8. Click **Save changes**.

### Example Policy

    {
      "Version": "2012-10-17",
      "Statement": [
        {
          "Sid": "AllowCloudFrontServicePrincipal",
          "Effect": "Allow",
          "Principal": {
            "Service": "cloudfront.amazonaws.com"
          },
          "Action": "s3:GetObject",
          "Resource": "arn:aws:s3:::video-streaming-bucket/*"
        }
      ]
    }

---

## Step 5: Test the Streaming Service

1. Go to the **CloudFront Distributions** page.
2. Wait until the distribution is deployed.
3. Copy the **Distribution domain name**.

Example:

    d111111abcdef8.cloudfront.net

4. Open a new browser tab.
5. Enter the CloudFront domain name.
6. Add the uploaded video file name at the end of the URL.

Example:

    https://d111111abcdef8.cloudfront.net/sample.mp4

7. Press **Enter**.
8. The video should load through the CloudFront stream.

---

## Result

The video streaming service was successfully created using **Amazon S3 and Amazon CloudFront**.
