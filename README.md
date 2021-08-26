# Documentation Repository for Tanzu Application Platform (TAP)

## Overview

This repo is expected to publish to https://docs-staging.vmware.com/en/VMware-Tanzu-Application-Service/0.1/tap-0-1

## Branches

| Branch | Usage |
|--------|-------|
| main | Development branch for beta docs |

## Product Names

There is a great variety of spellings and misspellings of product names.
JD suggests the following list:

* Cloud Native Runtimes for Tanzu
* Application Accelerator for Tanzu
* Application Live View for Tanzu
* Tanzu Build Service (not Service**s**)

Optionally, consider using the complete product name at first use:

* Cloud Native Runtimes for VMware Tanzu
* Application Accelerator for VMware Tanzu
* Application Live View for VMware Tanzu
* VMware Tanzu Build Service



## Word List

Use this table to keep a running list of terms used and how they should be defined.

| Word or phrase | Explanation |
|----------------|-------------|
| Package repository, PackageRepository, packagerepository, packageRepository | Are these all identical? If so, which formatting is correct? |
| PackageRepositories |  |
| PackageRepository CR | Is this a YAML file named `tap-package-repo.yml`? |
| PackageRepository Pull | |
| TAP repo bundle and TAP Repo Bundle| There are more instances of "TAP repo bundle" than "TAP Repo Bundle", so I'm assuming TAP repo bundle is correct.|
| Tanzu Application Platform packages | Why plural? Are there are multiple? "…install packages from the repository". How many packages are there?|
| TAP package repository |  How is this different from the other package repositories? (Are there non-TAP package repositories discussed on this page?) |
|  |  |

## Publishing docs
v0.1 Staging docs:  

- [docworks](https://docworks.vmware.com/) is the main tool for managing docs used by writers.
- [docsdash](https://docsdash.vmware.com/) is a deployment UI which manages the promotion from staging to pre-prod to production. The process below describes how to upload our docs to staging, replacing the publication with the same version.

### Prepare Markdown files
- Markdown files live in this repo.
- Each page requires an entry in [toc.md](docs/toc.md) for the table of contents.
- Images should live in an `images` directory at the same level and linked with a relative link.

### Create ZIP
Starting from the repo root, this will create a new `docs.zip` with no root folder and show its contents.

```sh
rm docs.zip ; cd docs && zip -r ../docs.zip * && cd .. && unzip -l docs.zip
```

### Upload the zip to docworks
- Go to https://docworks.vmware.com/md2docs/publish
- Fill in the fields exactly as below. Repeat this every time - the browser can help to remember form fields.
- Click on upload, and when prompted, enter your VMware AD password (for docsdash)
- If you see invalid path errors in the yellow box on the right there are broken links, but the site will still be published.
- If the toc.md is invalid then the site will not build, but there will be no indication that something is wrong.

### Form fields

|field|value|
|---|---|
|Publication name:   |`VMware Tanzu Application Service`|
|Product name:       |`VMware Tanzu Application Service`|
|Version:            |`0.1`|
|Publication GUID:   |`tap-0-1`|
|Output filename:    |`tap-0-1`|
|Output format:      |`HTML` (default)|
|Publication author  |`YOUREMAIL@vmware.com`|
|Publication language|`English`|
|Publish destination |`VMwareDocs` (default)|
|Publication audience|`None` (default)|
|PDF link            |`   ` (empty)|
|Zip File            |(choose the file)|

### In docsdash
- Wait about 1 minute for processing to complete after uploading.
- Go to https://docsdash.vmware.com/deployment-stage
- There should be an entry with a blue link which says `Documentation` and points to staging

### Promoting to Pre-Prod and Prod
- This may require additional privileges - reach out to Paige Calvert on the docs team [#tanzu-docs](https://vmware.slack.com/archives/C055V2M0H).
- Go to Staging publications in docsdash  
  https://docsdash.vmware.com/deployment-stage
- Select a publication (make sure it's the latest version)
- Click "Deploy selected to Pre-Prod" and wait for the pop to turn green (refresh if necessary after about 10s)
- Go to Pre-Prod list  
  https://docsdash.vmware.com/deployment-pre-prod
- Select a publication
- Click "Sign off for Release"
- Wait for your username to show up in the "Signed off by" column
- Select the publication again
- Click "Deploy selected to Prod"

### Landing page and publications
- Every product has a landing page
- The landing page is a container for all the "publications" for a product. Our first publication will be our combined docs for our first Beta, including installation, and user docs.
- Typically there will be a new docs publication for each minor release but not each point release. This version number become part of the URL e.g. Our first release was version `0.1` (see form section above for the current release).
- Some products like [TKG](https://docs.vmware.com/en/VMware-Tanzu-Kubernetes-Grid/index.html) publish separate release notes publications for each point release.
- For comparison see https://docs.vmware.com/en/VMware-Tanzu-Application-Catalog/index.html