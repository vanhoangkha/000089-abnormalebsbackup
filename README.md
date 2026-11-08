# AWS Backup anomaly detection for Amazon EBS volumes

> Detecting abnormal Amazon EBS backup activity.

A hands-on workshop from the [AWS First Cloud Journey](https://github.com/vanhoangkha/aws-first-cloud-journey) series, available in English and Vietnamese.

**Read the workshop online:** https://vanhoangkha.github.io/000089-abnormalebsbackup/

## Overview

Protecting your data from cyberattacks and ransomware is a critical responsibility, and taking the necessary steps to detect anomalous activity at every level within your organization can help you keep your data as safe as possible. Data storage is an important area where you can and should deploy anomaly detection.

To protect your storage, in this post I build a simple serverless pipeline to detect anomalies occurring on Amazon Elastic Block Store (EBS) volumes. I use AWS Backup along with several other AWS managed services to build the solution.

## Workshop contents

1. Introduction
2. Preparation
   - Create S3 bucket
   - Create EBS
   - Creating resources with CloudFormation
3. Check created resource
4. Createbackup
5. Create backup
6. Clean up resources

## Prerequisites

- An AWS account with permissions to create the resources used in the labs
- Basic familiarity with the AWS Management Console
- [Hugo](https://gohugo.io/installation/) (extended edition) if you want to run the site locally

## Run locally

```bash
git clone --recurse-submodules https://github.com/vanhoangkha/000089-abnormalebsbackup.git
cd 000089-abnormalebsbackup
hugo server
```

Then open http://localhost:1313 in your browser.

## Repository structure

| Path | Purpose |
| --- | --- |
| `content/` | Workshop pages (`*.md` English, `*.vi.md` Vietnamese) |
| `static/` | Images and other static assets |
| `layouts/` | Hugo layout overrides |
| `themes/` | Hugo theme |
| `config.toml` | Site configuration |

## Cost and cleanup

The labs create AWS resources that may incur charges. Complete the **Clean up** chapter when you finish to remove them.

## Contributing

Contributions are welcome. See [CONTRIBUTING.md](CONTRIBUTING.md).

To report a security issue, see [SECURITY.md](SECURITY.md).

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE).
