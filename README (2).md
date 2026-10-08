# Lab 10 — Deploy Static Web Application Using S3 on AWS

## Aim

To deploy a static web application using S3 on AWS and secure it with signed URLs.

## Requirements

- AWS Account
- Amazon S3
- Amazon CloudFront
- HTML
- CSS
- Web Browser

---

## Step 1: Create S3 Bucket

1. Login to the **AWS Management Console**.
2. Search for **S3**.
3. Open **Amazon S3**.
4. Click **Create bucket**.
5. Select the required **AWS Region**.
6. Enter a unique **Bucket name**.
7. Under **Block Public Access settings**, uncheck **Block all public access**.
8. Acknowledge the warning.
9. Keep the remaining settings as default.
10. Click **Create bucket**.

---

## Step 2: Enable Static Website Hosting

1. Open the newly created S3 bucket.
2. Click the **Properties** tab.
3. Scroll down to **Static website hosting**.
4. Click **Edit**.
5. Select **Enable**.
6. Select **Host a static website**.
7. Enter the following as the Index document:

   `index.html`

8. Click **Save changes**.

---

## Step 3: Create Website Files

Create the following folder structure:

    Lab10/
    ├── index.html
    └── style.css

### index.html

Create a file named `index.html` and add:

    <!DOCTYPE html>
    <html>
    <head>
        <title>Cloud Computing Lab 10</title>
        <link rel="stylesheet" href="style.css">
    </head>

    <body>

        <h1>Cloud Computing Lab 10</h1>

        <h2>Static Web Application</h2>

        <p>
            This website is deployed using Amazon S3
            and AWS CloudFront.
        </p>

        <button>Welcome to AWS</button>

    </body>
    </html>

### style.css

Create a file named `style.css` and add:

    body {
        font-family: Arial, sans-serif;
        text-align: center;
        background-color: lightblue;
        padding-top: 100px;
    }

    h1 {
        color: darkblue;
    }

    h2 {
        color: black;
    }

    p {
        font-size: 20px;
    }

    button {
        padding: 10px 20px;
        font-size: 16px;
    }

---

## Step 4: Add Bucket Policy

1. Open the S3 bucket.
2. Click **Permissions**.
3. Scroll down to **Bucket policy**.
4. Click **Edit**.
5. Add the following policy.
6. Replace `BUCKET_NAME` with your actual bucket name.

    {
      "Version": "2012-10-17",
      "Statement": [
        {
          "Sid": "PublicReadGetObject",
          "Effect": "Allow",
          "Principal": "*",
          "Action": "s3:*",
          "Resource": [
            "arn:aws:s3:::BUCKET_NAME/*",
            "arn:aws:s3:::BUCKET_NAME"
          ]
        }
      ]
    }

7. Click **Save changes**.

---

## Step 5: Upload Website Files

1. Open the S3 bucket.
2. Click **Objects**.
3. Click **Upload**.
4. Select the following files:

   `index.html`

   `style.css`

5. Click **Upload**.
6. Verify that both files are displayed in the bucket.

---

## Step 6: Test S3 Website

1. Go to the **Properties** tab.
2. Find **Static website hosting**.
3. Copy the **Bucket website endpoint**.
4. Open the endpoint in a web browser.
5. Verify that the website is displayed.

---

## Step 7: Create CloudFront Distribution

1. Open the **AWS Management Console**.
2. Search for **CloudFront**.
3. Open **CloudFront**.
4. Click **Create distribution**.
5. Under **Origin domain**, use the S3 static website URL.
6. Remove `https://` from the beginning if required.
7. Set the viewer protocol policy to:

   `Redirect HTTP to HTTPS`

8. Configure the allowed HTTP methods.
9. Click **Create distribution**.

---

## Step 8: Wait for CloudFront Deployment

1. Open the **CloudFront Distributions** page.
2. Find your newly created distribution.
3. Wait until the distribution status becomes **Deployed**.

---

## Step 9: Open CloudFront Website

1. Copy the **Distribution domain name**.
2. Open a new browser tab.
3. Enter the CloudFront URL.

Example:

    https://xxxxxxxxxxxx.cloudfront.net

4. The static website should be displayed.

---

## Step 10: Verify Output

The website should display:

**Cloud Computing Lab 10**

**Static Web Application**

This website is deployed using Amazon S3 and AWS CloudFront.

**Welcome to AWS**

---

## Experiment Flow

    AWS Management Console
            ↓
        Amazon S3
            ↓
      Create S3 Bucket
            ↓
    Enable Static Website Hosting
            ↓
      Create Website Files
            ↓
       Add Bucket Policy
            ↓
      Upload Website Files
            ↓
       Test S3 Website
            ↓
       Amazon CloudFront
            ↓
      Create Distribution
            ↓
     Wait for Deployment
            ↓
    Copy CloudFront Domain
            ↓
       Open Website

---

## Result

The static web application was successfully deployed using **Amazon S3** and accessed through **Amazon CloudFront**.

---

## Conclusion

Amazon S3 was used to store and host the static website files. Static website hosting was enabled, a bucket policy was configured, the website files were uploaded, and Amazon CloudFront was used to distribute the website.
