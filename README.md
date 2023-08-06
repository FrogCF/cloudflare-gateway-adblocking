# Cloudflare Gateway Adblocking  
Serverless adblocking via Cloudflare Zero Trust Gateway  

### What is this?  
This is a serverless adblocking solution that uses Cloudflare's Zero Trust Gateway to block ads by parsing a hosts file and creating a firewall rule to block the domains. It can be used as an alternative to Pi-Hole or other adblocking solutions.  
This project was heavily inspired by [this blog post](https://blog.marcolancini.it/2022/blog-serverless-ad-blocking-with-cloudflare-gateway/)  


### Pre-requisites
* Python > 3.10  
* A Cloudflare account with Zero Trust enabled  
* A Cloudflare API tolken with the following permissions:  
    * Zero Trust: Edit  
    * Account Firewall Access Rules: Edit  
    * Access: Apps and Policies: Edit  
* A device with the WARP client installed and configured to use a Zero Trust account  

<!-- 
### Installation  
#### From PyPi  
`pip install cloudflare-gateway-adblocking`
 -->

### Usage   
#### Setting Cloudflare credentials  
##### Environment variables  
The following environment variables can be used to set the Cloudflare credentials:  
* `CLOUDFLARE_ACCOUNT_ID`
* `CLOUDFLARE_TOKEN`  
These can either be set in the environment or in a `.env` file in the current working directory.  
#### Command line flags  
The following command line flags can be used to set the Cloudflare credentials:
* Cloudflare Account ID: `--account-id` / `-a`  
* Cloudflare Token: `--token` / `-t`  
#### Passing blocklists  
Blocklists can be passed to the program via the command line flag `--blocklist` / `-b`. This flag can either point to a hosts file or a directory containing hosts files. If this flag is not passed, the program will look for a file or directory named `blocklists` in the current working directory.  
#### Uploading blocklists and creating a firewall policy
To upload the blocklists to Cloudflare and create a firewall policy, use the `upload` subcommand.  
For example:  
`cloudflare-gateway-adblocking upload`  
#### Deleting blocklists and firewall policy  
To delete the blocklists from Cloudflare and delete the firewall policy, use the `delete` subcommand.  
For example:  
`cloudflare-gateway-adblocking delete`  