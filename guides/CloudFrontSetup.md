# CloudFront Setup Guide

## Introduction
This guide details the process of setting up an AWS CloudFront distribution to deliver your website content globally. Using CloudFront not only improves site performance through faster load times but also enhances security by integrating with AWS WAF and SSL/TLS.

## Prerequisites
- A static website hosted on AWS S3.
- An SSL/TLS certificate managed through AWS Certificate Manager (ACM).

## Steps

### 1. Creating a CloudFront Distribution
- **Navigate to the CloudFront Dashboard**:
  - Open the AWS Management Console.
  - Go to the CloudFront service section.
- **Create Distribution**:
  - Click on `Create Distribution`.
  - Choose `Web` as the delivery method for your content.
  - Click `Get Started`.

### 2. Configure Distribution Settings
- **Origin Settings**:
  - **Origin Domain Name**: Select your S3 bucket from the drop-down list or enter your S3 bucket's static website endpoint.
  - **Origin ID**: This will be auto-filled based on your selection.
- **Default Cache Behavior Settings**:
  - **Viewer Protocol Policy**: Choose `Redirect HTTP to HTTPS` to enforce secure connections.
  - **Allowed HTTP Methods**: Select `GET, HEAD, OPTIONS, PUT, POST, PATCH, DELETE`.
  - **Field-level Encryption Config**: Optional, select if required.
- **Distribution Settings**:
  - **Price Class**: Choose the price class that best fits your audience location.
  - **Alternate Domain Names (CNAMEs)**: Enter your domain names (e.g., `example.com` and `www.example.com`).
  - **SSL Certificate**: Select the SSL/TLS certificate you previously configured in ACM.
  - **Default Root Object**: Typically `index.html` or the entry point of your site.
  - **Logging**: Enable logging if you wish to monitor access and errors. Specify an S3 bucket for log storage.

### 3. Deploying the Distribution
- Review all settings to ensure they are correct.
- Click `Create Distribution`.
- The distribution will now be created, and its status will change from `In Progress` to `Deployed` when ready, which may take several minutes.

### 4. Configuring DNS to Use CloudFront
- **Return to Route 53**:
  - Navigate to your domain’s hosted zone.
  - Update DNS records to point to your CloudFront distribution.
    - For the apex domain, create an Alias record pointing to the CloudFront distribution after selecting "Yes." for Alias.
    - Update the 'www' version of the CNAME record to point to the CloudFront distribution’s DNS name, replace the record name with 'www' and the value with the CloudFront distribution’s DNS name.

### 5. Testing and Validation
- Test your domain by accessing it through a browser. Ensure the site is loading correctly over HTTPS and served through CloudFront.
- Use tools like `dig` or `nslookup` to verify DNS records are correctly resolving to CloudFront.

## Conclusion
With AWS CloudFront configured, your website should now be more accessible and secure, delivering content efficiently to users worldwide.
