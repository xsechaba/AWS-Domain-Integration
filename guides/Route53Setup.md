# Route 53 Setup Guide

## Introduction
This guide provides step-by-step instructions on how to create a hosted zone in AWS Route 53, connect a domain purchased from GoDaddy, and configure DNS settings to integrate with AWS CloudFront. This is a critical part of setting up your website to ensure it is accessible by your custom domain and benefits from AWS services.

## Prerequisites
- An active AWS account.
- A domain name registered with GoDaddy.
- Basic knowledge of DNS management.

## Steps

### 1. Creating a Hosted Zone in Route 53
- **Login to AWS Management Console**: Navigate to the Route 53 dashboard.
- **Create Hosted Zone**: Click on `Create Hosted Zone`.
  - **Domain Name**: Enter your domain name (e.g., `yourdomain.com`).
  - **Type**: Select `Public Hosted Zone`.
  - Click `Create`.
- After creation, note the NS (Name Server) records provided by AWS. These will be used to update the nameserver settings in GoDaddy.

### 2. Updating Nameservers in GoDaddy
- **Login to GoDaddy**: Access your domain management dashboard.
- **Find Your Domain**: Navigate to the DNS settings for your domain.
- **Modify Nameservers**:
  - Replace the current nameservers with the AWS Route 53 NS records.
  - Save the changes.
- This may take some time - for these changes to propagate over the internet.

### 3. Configuring DNS Records for CloudFront
- Return to the Route 53 dashboard in your AWS console.
- Select your hosted zone and click on `Create Record Set` for the following configurations:

  - **A Record for Apex Domain**:
    - **Name**: Leave blank for the apex domain.
    - **Type**: A – IPv4 address.
    - **Alias**: No.
    - Click `Save Record Set`.
