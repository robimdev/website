---
layout: post
title: "Troubleshooting SSH Key Revocation in Google Cloud Cloned Drive"
excerpt: I'll share a recent experience I had with Google Cloud. After cloning a drive, I found that the SSH keys were revoked after 30 days. It took me 5 hours to figure out what had happened and how to resolve it.
date: 2023-07-04
categories: [Tech, Reviews]
---

## Troubleshooting SSH Key Revocation in Google Cloud Cloned Drive

In this blog post, I'll share a recent experience I had with Google Cloud. After cloning a drive, I found that the SSH keys were revoked after 30 days. It took me 5 hours to figure out what had happened and how to resolve it. I hope that by sharing this, I can save others the same headache.

## The Problem

Everything was running smoothly until one day, I couldn't connect via SSH anymore. The website would just timeout. I was puzzled and started looking for clues.

## The Investigation

I turned to the logging section of the Google Cloud Platform. There, I noticed that the SSH keys were marked with red, indicating errors. This was a crucial clue.

## The Culprit

Upon inspecting the actual key string, I found something interesting. In between curly brackets at the end of the string, there was a tag that set the expiry date. It turned out that the SSH keys were set to expire after 30 days. This was why my SSH connection was failing.

It's worth noting that this disk was a clone, attached to a new VM. It seems that Google Cloud Platform adds this expiry tag to SSH keys that are a clone of the main disk as a security measure. Therefore, the SSH keys expire after 30 days since the clone was made.

## The Solution

Once I identified the problem, the solution was straightforward. I had two options:

1. Edit the key string to extend the expiry date.
2. Generate a new key and add it to my VM.

I chose the second option. After generating a new key and adding it to my VM, I was able to connect via SSH again. The website was back up and running.

## Conclusion

This experience taught me the importance of paying attention to the details. Something as small as an expiry date tag in a key string can cause significant problems. I hope that by sharing this, I can help others who might face the same issue.
