## CloudFront

Amazons Content Delivery Network (CDN).

Is focused on content delivery, i.e. more efficient reads/downloads.

Transfer acceleration is focused on enabling faster uploads to S3.

Origins are the source of the files, they can be S3, EC3, ELB or Route53.

Web distribution is typically for websites, RTMP is used for media streaming. You can also use CloudFront for a non-AWS origin server (on-prem server).

You can restrict access to content by using signed URLs or signed cookies.

### Edge Locations

Edge locations are caches of the main server but does have a TTL and may not be faster for the first request. You can clear the cache manually but you will be charged, you can also invalidate files that you do not want distributing but you are also charged for this. They are separate to a region or availability zone. Distribution is the name for the CDN, which is a collection of edge locations. There are 300+ Edge location is 90+ cities across nearly 50 countries.

### S3 Performance Optimisation

If you use S3 and are read heavy you can use CloudFront.
