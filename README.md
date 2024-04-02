
## Official DISA STIG for Canonical Ubuntu 20.04 LTS

To access the official DISA STIG for Canonical Ubuntu 20.04 LTS, follow these steps:

1. Visit the [DISA STIG Downloads](https://public.cyber.mil/stigs/downloads/) page.

2. Use the search functionality to find "Canonical Ubuntu 20.04 LTS STIG — Ver 1, Rel 9."

3. Download the STIG document to review and implement the security guidelines.

## Getting Started

# OpenSCAP and SCAP Security Guides Installation Guide for Ubuntu Server

## Introduction

STIG, or Security Technical Implementation Guide, is a set of hardware and software configuration standards developed by the Defense Information Systems Agency (DISA). Compliance with STIGs is mandatory for all DoD agencies and organizations using DoD information networks. OpenSCAP, in conjunction with SCAP (Security Content Automation Protocol) tools, automates STIG compliance scans.

## What is SCAP?

SCAP is a standardized protocol for security automation that facilitates the automation of security-related tasks such as vulnerability scanning, configuration assessment, and compliance checks.

## What is OpenSCAP?

OpenSCAP is an open-source tool that leverages SCAP standards to automate the assessment and validation of STIG compliance.

## Key SCAP Components:

- **OVAL (Open Vulnerability and Assessment Language):** Standardized language for sharing information on vulnerabilities and security configurations.
- **XCCDF (Extensible Configuration Checklist Description Format):** Standard format for expressing security checklists and configuration baselines.
- **OCIL (Open Checklist Interactive Language):** Language for expressing interactive questions in security checklists.
- **CPE (Common Platform Enumeration):** Standardized method for naming and identifying hardware, software, and operating systems.
- **CCE (Common Configuration Enumeration):** Standardized method for identifying and classifying security-relevant configuration issues.
- **CVE (Common Vulnerabilities and Exposures):** Dictionary of publicly known information security vulnerabilities and exposures.
- **CVSS (Common Vulnerability Scoring System):** Framework for assessing the severity of security vulnerabilities.

## Installing OpenSCAP on Ubuntu Server

```bash
$ sudo apt update
$ sudo apt install libopenscap8
$ wget https://security-metadata.canonical.com/oval/com.ubuntu.$(lsb_release -cs).usn.oval.xml.bz2
$ bunzip2 com.ubuntu.focal.usn.oval.xml.bz2
$ oscap oval eval --report cve_report.html com.ubuntu.focal.usn.oval.xml
```
## Install SCAP Security Guides
```bash
$ sudo git clone https://github.com/pkpraveen267/Ubuntu-Scap-security-guide.git
$ cd scap-security-guide-0.1/ssg_guide_ubuntu
$ oscap info ssg-ubuntu2004-ds-1.2.xml
$ sudo oscap xccdf eval --profile xccdf_org.ssgproject.content_profile_stig --report report.html ssg-ubuntu2004-ds-1.2.xml
```
## Interactive User Guide

   # Update System:
        Run sudo apt update to ensure your system is up to date.

  # Install OpenSCAP:
        Install OpenSCAP using sudo apt install libopenscap8.

  #  Download OVAL Content:
        Download OVAL content for your Ubuntu version.
```bash
$ wget https://security-metadata.canonical.com/oval/com.ubuntu.$(lsb_release -cs).usn.oval.xml.bz2
$ bunzip2 com.ubuntu.focal.usn.oval.xml.bz2
```
## Scan the System:

   # Use OpenSCAP to scan your Ubuntu system.
```bash
$ oscap oval eval --report cve_report.html com.ubuntu.focal.usn.oval.xml
```
## Install SCAP Security Guides:

  # Clone the SCAP Security Guide repository.

```bash

$ sudo git clone https://github.com/pkpraveen267/Ubuntu-Scap-security-guide.git
$ cd scap-security-guide-0.1/ssg_guide_ubuntu
```
## Evaluate STIG Profile:

   # Use OpenSCAP to evaluate the STIG profile and generate a report.

```bash

$ sudo oscap xccdf eval --profile xccdf_org.ssgproject.content_profile_stig --report report.html ssg-ubuntu2004-ds-1.2.xml
```
## Ensure to replace ssg-ubuntu2004-ds-1.2.xml with the correct file for your Ubuntu version ##
