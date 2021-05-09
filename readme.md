# URL Lookup Service

## API Reference

### URL Lookup
```sh
GET /urlinfo/1/:hostname/:path
```
#### Response
```js
{ message: "", safe: true }
```
### Update MALWARE
```sh
POST /update_malwares
```
#### Payload
- arrays of url
```
['example.com', 'google.com/keep?auth=2', 'mail.yahoo.com']
```
#### Response
```
{
    status : "success", message: ""
}
```
### PART 2

1.   To scale this Lookup Service beyond the memory capacity of the system the use of a process manager would be the best option for me alternatively i might deploy this service as a serverless function
2.   The best way to go about it in my experience when the system are distributed in different regions is to do so at the networking level with a load balancer.
   
   If this service where to be hosted on Amazon Web Services, i would use the built-in Elastic Load Balancing, which also includes auto-scaling and many more features.
   
   ### For example:

   * You can add version headers to the request and have the load balencer direct requests to the correct version of the service.

   * You can have blue/green groups of servers which you take out for no down time upgrades

   * You can assign load based on each servers response time
   
   

3.  In the problem statement, the REST API supports bulk URL updates. JSON is used for the simplicity, CSV will be more efficient.
4.  If i wake up 3am, the first thing to do is the health check for the app and check the mempry usuage.
5.  No, the change wont affect anything in app.
6.  some consideration for the lifecycle of this app are, CI-Continuous Integration, CD-Continuous Deplyment/delivery, CT, Continuous Test, CM- Continuous Monitoring.

7.  I would follow the general standard which is to always base line your service urls with a version.

    Eg,

    ``` /v1/account/getUserInfo ```

    If you need to release a new version, expose it over:

    ``` /v2/account/getUserInfo ```

    Where v2 can run over a different branch of the codebase.

