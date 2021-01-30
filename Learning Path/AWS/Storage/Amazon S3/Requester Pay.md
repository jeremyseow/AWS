# Requester Pay

- When this feature is enabled, any costs associated with requests and data transfer becomes the responsibility of the requester instead of the bucket owner

- The bucket owner will still, however, pay for the storage costs associated with the objects stored in the bucket

- A fundamental condition of enabling requester pays is ensuring that all access is authenticated to your bucket, as anonymous access requests will not be able to take advantage of the requester pays attribute
	- By authenticating requests, it allows a trace back to the identity and to which AWS account that identity is originating from, and the cost is then transferred to that account

- Any POST, GET or HEAD requests to the bucket must include x-amz-request-payer in the header and this parameter confirms that the requester is aware that there are cost implications associated with that request for requester pays