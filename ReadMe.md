
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

**Install SCAP Security Guides**

In addition to OpenSCAP, we need to install the SCAP Security Guide (SSG) for our Debian-based system.

SSGs are security policies that transform STIGs (and other security guidelines) into a machine readable format (XCCDF) that can be used by OpenSCAP to scan your system for vulnerabilities and compliance.

We need the guide for Ubuntu 20.04. To get this, we can download the latest SSG packages from the ComplianceAsCode project

- Download the latest Scap Security Guide

**$ sudo git clone https://github.com/security-guide.git**

- Extract scap-security-guide-0.1.tar.bz2 file and go to ssg\_guide\_ubuntu directory **$ cd scap-security-guide-0.1/ssg\_guide\_ubuntu**
- Display a list of available Profiles **oscap info ssg-ubuntu2004-ds-1.2.xml**

![](Aspose.Words.66189251-f414-4fb6-b2ba-3a844dc22399.001.jpeg)

**Use OpenSCAP to Evaluate the Security Policy and Profile**

We will scan our Ubuntu system using the xccdf\_org.ssgproject.content\_profile\_stig profile and the ssg-ubuntu2004-ds-1.2.xml security policy.

- Evaluate a STIG Profile and write XCCDF results into a report.html file

**$ sudo oscap xccdf eval --profile xccdf\_org.ssgproject.content\_profile\_stig --report report.html ssg-ubuntu2004-ds-1.2.xml**

**sudo oscap xccdf eval:** Indicates to evaluate the compliance of the system against the rules specified in the XCCDF file.

**--profile xccdf\_org.ssgproject.content\_profile\_stig:** Specifies to use the xccdf\_org.ssgproject.content\_profile\_stig profile, which represents the Ubuntu 20.04 STIG configuration.

**--report report.html:** Indicates to save the compliance evaluation results of the scan in HTML format in a new document called report.html.

**ssg-ubuntu2004-ds-1.2.xml**: Indicates the XCCDF content file against which the system's compliance is being evaluated.
