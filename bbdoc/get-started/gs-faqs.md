# Frequently Asked Questions \(FAQs\)

## General

How do I generate a JWT token? See \[CLI Authentication\]\(cli-authentication\).

How does paging work for listing APIs? The Illumina Analytics Platform utilizes token-based paging. The initial call to an endpoint that supports paging will return a set of page tokens that can be utilized to navigate the returned records. Up to four tokens may be returned: \* \*nextPageToken\*: Will take you forward one page. \* \*previousPageToken\*: Will take you back one page. \* \*firstPageToken\*: Will take you to the first page of records. \* \*lastPageToken\*: Will take you to the last page of records. This token is not returned by default, as it is computationally expensive and will slow the initial response down. To include this token in the response, add the "&include=totalItemCount" query parameter to the request. When the nextPageToken field is null, there are no more records in the list. The previous page token is null on the first page. The default page size is 10. However, the pageSize parameter can optionally be set to a value from 1 to 1000, inclusive. Following the initial request to set the pageSize, pageSize cannot be changed and still utilize the same navigation tokens provided in the initial response. \#\#\# Paging parameters \* \*pageSize\*: Optional parameter to define the number of records returned per response. Valid value must be in the range 1-1000. \* \*pageToken\*: Optional parameter for navigation after initial listing. Valid values include firstPageToken, nextPageToken, and previousPageToken \(provided in the list response\). \* \*sort\*: Optional parameter to set the sort order of the returned list. The sort can be specified as ascending \(default\) or descending. Depending on the endpoint, the default sort field may vary. \(ie, &sort=sort-key-value \[asc\|desc\]\)

## Data Management

When do my temporary credentials expire? When requesting temporary upload credentials to AWS for file or folder upload, the returned credentials expire after 36 hours.

How do I upload additional files to a folder after my temporary credentials expire? If your credentials expire, you'll need to PATCH the original folder for new temporary credentials to continue uploading to that path.

I'm filtering my files list by a path and don't see my files. How can I see my files? To filter by path and see the files, the end of your path must end in "\*". Without the wildcard character, the filter only looks for exact matches.

How do I upload files to the root folder of my volume? To get upload credentials to the root folder of a volume, the ID of the root folder is required. To retrieve the root folder ID, use the following query: GET v1/folders?volume.name={volumeName}&path="/" The query returns exactly one record. Use the returned ID with PATCH v1/folders/{Id} and the include=objectStoreAccess parameter to get upload credentials to the root folder.

Can I upload an empty folder via the AWS CLI and see it in GDS? No. AWS S3 is an object store, which requires an actual object to exist at the key. To view a folder in GDS, upload the folder with content.

## Command-line Interface

When I launch the CLI for the first time, I get errors indicating it could not create the configuration folder and config file in the user home directory? In Windows this issue can be seen when running the terminal in Administrative mode. Run the Windows terminal outside of Administrative mode to resolve this issue.

