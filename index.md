---

layout: col-sidebar
title: OWASP Dependency-Check
site_side: true
tags: dependency-check sca cpe purl vulnerability
level: 4
type: tool
pitch: Dependency-Check is a software composition analysis utility that identifies project dependencies and checks if there are any known, publicly disclosed, vulnerabilities.

---

Dependency-Check is a Software Composition Analysis (SCA) tool that attempts to detect publicly disclosed vulnerabilities contained within a project's dependencies. It does this by determining if there is a Common Platform Enumeration (CPE) identifier for a given dependency. If found, it will generate a report linking to the associated CVE entries.

## Introduction

The OWASP Top 10 2013 contains a new entry: A9-Using Components with Known Vulnerabilities. Dependency Check can currently be used to scan applications (and their dependent libraries) to identify any known vulnerable components.

The problem with using known vulnerable components was described very well in a paper by Jeff Williams and Arshan Dabirsiaghi titled, "[Unfortunate Reality of Insecure Libraries](https://cdn2.hubspot.net/hub/203759/file-1100864196-pdf/docs/Contrast_-_Insecure_Libraries_2014.pdf)". The gist of the paper is that we as a development community include third party libraries in our applications that contain well known published vulnerabilities (such as those at the [National Vulnerability Database](https://nvd.nist.gov/vuln/search).

Dependency-check has a command line interface, a Maven plugin, an Ant task, and a Jenkins plugin. The core engine contains a series of analyzers that inspect the project dependencies, collect pieces of information about the dependencies (referred to as evidence within the tool). The evidence is then used to identify the [https://nvd.nist.gov/products/cpe Common Platform Enumeration (CPE)] for the given dependency. If a CPE is identified, a listing of associated [Common Vulnerability and Exposure (CVE)](https://cve.mitre.org/) entries are listed in a report.

Dependency-check automatically updates itself using the [NVD Data Feeds](https://nvd.nist.gov/vuln/data-feeds) hosted by NIST. '''IMPORTANT NOTE:''' The initial download of the data may take ten minutes or more. If you run the tool at least once every seven days, only a small JSON file needs to be downloaded to keep the local copy of the data current.
