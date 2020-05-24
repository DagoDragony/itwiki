# OAuth

Open Authorization(OAuth) was created for services to be able to authorize on your behalf
However, sometimes it is used for authentication too

* Resource owner
* Client - service that wants to get access to resources
* Resource server
* Authorization server - issues access tokens to the clients

## Flows
### Authorization Code Flow

Theoretically safest way

* Resource owner tells PhotoPrinting service that it want access GoogleDrive photos
* Photo printing service(client) tells google authorization service that user want's access to photos
* Authorization service loads page and asks resource owner if it want's to allow access to photos.
* If user accepts, it sends a client(photo printing service) Auth token
* Client uses that Auth token and access authorization service to get second token(Access token) - sth client hold on to
* With access token client calls the resource server directly
* Resource server checks validity of access token and if everything ok, it provices what client asks

### Implicit Flow

The same as in Authorization Code Flow, but this time, authentication server returns access token(skips authorization token)
Other steps are the same

Drawback:
more prone to interception

Usually used for javascript apps

### Client Credentials Flow

Authorication between microservices
Used when the client is well trusted(confidential clients)

* Microservice1 calls authenticatino service and provice special key
* Authorization gives access token for specific resources
* Microservice1 gives access token to Microservice2
* Microservice2 checks if access token is valid for asked resources and returns what is asked if valid
