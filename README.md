# get_aws_dns_validated_certificate
A Terraform module to create an AWS ACM certificate validated by DNS.

## Description
This module creates an AWS ACM certificate, using DNS to validate domain ownership.

## Inputs
1. dns_domain_name (string) - The domain name for the Route 53 hosted zone
2. certificate_domain_name (string) - The domain name for this certificate
3. certificate_san (string) - The subject alternative name(s) for this certificate
4. certificate_tags (map) - Tags to apply to this certificate
5. is_cloudfront_certificate (bool) - If true, the certificate will be created in North Virginia (us-east-1) for use with a CloudFront distribution

## Usage
```hcl
module "get_certificate" {
  source = "git@github.com:robinvenables/get_aws_dns_validated_certificate.git"

  dns_domain_name         = "robinvenables.com"
  certificate_domain_name = "robinvenables.com"
  certificate_san         = ["www.robinvenables.com"]
  certificate_tags = {
    Name    = "venables-website-certificate"
  }
  is_cloudfront_certificate = true
}
```

## Outputs
1. The ARN of the newly generated certificate
