# AWS Domain Integration

## Project Overview
This repository is a continuation of a separate project detailing [how to host a static website](https://github.com/xsechaba/aws-website-hosting/tree/main) using AWS. It focuses on the subsequent steps required to secure and optimize the website by configuring a domain, SSL/TLS certificate, and content delivery through AWS CloudFront. The domain for this project is acquired from GoDaddy and integrated into AWS services using Route 53.

## Technologies Used
- AWS S3 (Simple Storage Service)
- AWS CloudFront
- AWS Route 53
- AWS Certificate Manager (ACM)
- GoDaddy (Domain provider)

## Project Components

### Domain Configuration and DNS Setup
- **Hosted Zone Creation**: Using AWS Route 53 to manage DNS records.
- **Domain Integration**: Connecting a GoDaddy domain with AWS by updating DNS settings in Route 53.
  
### Security with SSL/TLS Certificates
- **Certificate Request**: Using AWS Certificate Manager to request and validate an SSL/TLS certificate.
- **DNS Validation**: Configuring DNS to validate the SSL/TLS certificate ensuring the domain ownership.

### Content Delivery with CloudFront
- **CloudFront Distribution**: Setting up CloudFront to deliver the website content globally.
- **DNS Configuration**: Adjusting DNS records to route traffic through CloudFront, ensuring efficient content delivery.

### Testing and Verification
- **DNS Propagation**: Checking the DNS propagation to ensure the domain correctly points to the CloudFront distribution.
- **HTTPS Enforcement**: Ensuring that the site is accessible securely via HTTPS and that all configurations are correctly applied.

## Guides
Detailed guides are provided to walk through each step of the setup and configuration process:
- [Creating and Configuring the Hosted Zone in Route 53](/guides/Route53Setup.md)
- [Requesting and Validating SSL/TLS Certificates](/guides/CertificateSetup.md)
- [Setting up CloudFront for Content Delivery](/guides/CloudFrontSetup.md)
- [DNS Configuration and Testing](/guides/DNSConfigurationTesting.md)

## Troubleshooting
A section dedicated to common issues encountered during the deployment and their resolutions:
- [Common Issues and Fixes](/troubleshooting/CommonIssues.md)

## Conclusion
This project aims to document the detailed steps involved in deploying a secure and optimized static website using AWS, from setting up SSL/TLS certificates to integrating with a third-party domain provider like GoDaddy and leveraging AWS CloudFront for global content delivery.

## Author
- Sechaba Mohlabeng
