# SSL/TLS Certificate Setup Guide

## Introduction
This guide explains how to request and validate an SSL/TLS certificate through AWS Certificate Manager (ACM), using DNS validation with AWS Route 53. Utilizing Route 53 for DNS validation can significantly speed up the certificate validation process.

## Prerequisites
- An active AWS account.
- A domain managed in AWS Route 53.

## Steps

### 1. Requesting an SSL/TLS Certificate
- **Navigate to AWS Certificate Manager**:
  - Open the AWS Management Console.
  - Go to the ACM (AWS Certificate Manager) section.
- **Request a Certificate**:
  - Click on `Request a certificate`.
  - Select `Request a public certificate` and click `Next`.
  - **Add domain names**:
    - Enter your domain name (e.g., `yourdomain.com`) and any subdomains (e.g., `www.yourdomain.com`) as needed.
  - Click `Next`.

### 2. Selecting the Validation Method
- **Choose DNS Validation**:
  - Opt for DNS validation as it allows you to validate domain ownership by adding a CNAME record to your DNS configuration.
  - Click `Review` and then `Confirm and request`.

### 3. Configuring DNS Records in Route 53
- **Set Up DNS Records**:
  - Once you've requested the certificate, ACM will provide you with one or more CNAME records.
  - Open a new browser tab and navigate to the Route 53 dashboard in the AWS Console.
  - Select your domain’s hosted zone.
  - Click `Create records` to automatically add the CNAME records provided by ACM to Route 53.
    - This automation speeds up the process by correctly formatting and entering the DNS records required for validation.
  - Go back to the ACM dashboard and click `Create records in Route 53` which simplifies and expedites the validation.

### 4. Certificate Validation
- **Validation Process**:
  - After adding the CNAME records, ACM will automatically check for the presence of these records and validate your domain ownership.
  - This process can take from a few minutes to several hours - it luckily too just 15 minutes for me. You can check the status of your certificate request in the ACM dashboard under `Certificates`.

### 5. Using Your Certificate
- Once validated, the certificate will be issued and can then be associated with Amazon CloudFront to enable HTTPS.

## Conclusion
By following these steps, your SSL/TLS certificate should be requested, validated, and ready to use with your AWS applications, ensuring secure communications for your domain.

## Additional Resources
- [AWS Certificate Manager Documentation](https://docs.aws.amazon.com/acm/)
- [AWS Route 53 Documentation](https://docs.aws.amazon.com/Route53/)
