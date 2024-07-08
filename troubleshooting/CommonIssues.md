# Common Issues and Solutions

## Introduction
This document outlines common issues faced during the deployment of websites on AWS using services like Route 53, CloudFront, and AWS Certificate Manager (ACM), along with solutions and troubleshooting tips to help resolve these issues efficiently.

## Issues and Solutions

### 1. Delayed SSL/TLS Certificate Validation
**Issue**: Certificate validation via AWS Certificate Manager (ACM) takes longer than expected.
**Solution**:
- **Speed Up Validation**: Utilize the "Create records in Route 53" feature during the DNS validation process. This feature allows you to automatically create the required DNS records directly within Route 53, ensuring they are correctly formatted and speeding up the validation process.
- **Check DNS Configuration**: Ensure that the DNS records (CNAME) provided by ACM during the setup are correctly entered in your DNS configuration. Incorrect entries can prolong or block validation.

### 2. DNS Propagation Delays for `www` Subdomain
**Issue**: Accessing the website via the `www` version (e.g., `www.example.com`) shows "site cannot be reached" soon after DNS changes.
**Solution**:
- **Patience During Propagation**: DNS changes, especially for new records or updates, can take up to 48 hours to fully propagate worldwide. During this time, intermittent access issues can occur.
- **Check DNS Settings**: Verify that the CNAME record for the `www` subdomain is correctly pointing to your CloudFront distribution. Incorrect or missing records can cause the domain to not resolve properly.
- **Use DNS Tools**: Tools like `dig` or `nslookup` can help you check the current state of DNS propagation and verify that your records are set up correctly.

### 3. CloudFront Distribution Not Serving Content
**Issue**: After setting up a CloudFront distribution, the content does not seem to be delivered from the distribution.
**Solution**:
- **Check Origin Settings**: Ensure that the CloudFront distribution is correctly pointed to your S3 bucket or other origins. The origin domain name must match exactly what was specified when the distribution was created.
- **Verify Behaviors**: In CloudFront, check that the cache behavior settings are correctly configured to handle viewer requests, including path patterns and protocols.
- **SSL/TLS Certificate**: Make sure that the SSL/TLS certificate associated with your CloudFront distribution covers both the root domain and any subdomains used.

### 4. HTTPS Redirection Not Working
**Issue**: HTTP requests are not being redirected to HTTPS, leading to security warnings or mixed content issues.
**Solution**:
- **Adjust CloudFront Settings**: Ensure that the viewer protocol policy in your CloudFront distribution is set to "Redirect HTTP to HTTPS". This setting forces all incoming HTTP requests to be redirected to HTTPS.
- **Check Route 53 Records**: For redirection to work correctly, ensure that DNS records in Route 53 are properly configured to point to your CloudFront distribution which handles the redirection.

## Conclusion
Deploying websites on AWS can involve complex configurations and settings. When issues arise, it's important to methodically review configurations, verify settings, and use available tools to diagnose and resolve problems. Regular monitoring and adjustments can help maintain the stability and performance of your site.
