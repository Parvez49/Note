
from rest_framework import status
from rest_framework.response import Response



### Success Responses
```
1. status.HTTP_200_OK ->  The request was successful. Often used for successful GET, PUT, PATCH, and DELETE operations.
2. status.HTTP_201_CREATED -> The request resulted in a new resource being created. Typically used for POST requests.
3. status.HTTP_202_ACCEPTED -> This status code is returned when a request has been accepted for processing, but the processing has not been completed. It is often used when background tasks (like Celery tasks) are involved.
4. status.HTTP_204_NO_CONTENT  -> The request was successful, but there is no content to return. Often used for DELETE requests.
5. status.HTTP_206_PARTIAL_CONTENT -> This status code is used when only a portion of the resource is returned, such as when serving paginated results or a range of bytes from a file.
```


### Client Error Responses
```
1. status.HTTP_400_BAD_REQUEST -> The request was invalid or cannot be served. when the client sends invalid data.
    return Response({'error': 'Invalid data'}, status=status.HTTP_400_BAD_REQUEST)

2. status.HTTP_401_UNAUTHORIZED -> Authentication is required and has failed or has not been provided.
    return Response({'error': 'Authentication required'}, status=status.HTTP_401_UNAUTHORIZED)

3. status.HTTP_403_FORBIDDEN -> 
    return Response({'error': 'Permission denied'}, status=status.HTTP_403_FORBIDDEN)

4. status.HTTP_404_NOT_FOUND -> The requested resource could not be found. (Invalid URL)
    return Response({'error': 'Not found'}, status=status.HTTP_404_NOT_FOUND)

5. status=status.HTTP_405_METHOD_NOT_ALLOWED -> the method used in the request (e.g., POST, GET, PUT) is not allowed for the requested resource.
    return Response({'error': 'Method not allowed'}, status=status.HTTP_405_METHOD_NOT_ALLOWED)

6. status.HTTP_406_NOT_ACCEPTABLE -> This is returned when the server cannot generate a response that matches the list of acceptable values defined in the request's Accept header.
    return Response({'error': 'Not acceptable'}, status=status.HTTP_406_NOT_ACCEPTABLE)

7. status.HTTP_409_CONFLICT -> This status code is used when there is a conflict with the current state of the resource, such as when trying to create a duplicate record.

8. status.HTTP_429_TOO_MANY_REQUESTS -> This status is returned when the client has sent too many requests in a given period (rate limiting).
```


### Server Error Responses
```
1. status.HTTP_500_INTERNAL_SERVER_ERROR -> The server encountered an error and could not complete the request.

2. status.HTTP_501_NOT_IMPLEMENTED -> This status code is returned when the server does not recognize the request method or lacks the ability to fulfill it. 
    return Response({'error': 'Not implemented'}, status=status.HTTP_501_NOT_IMPLEMENTED)

3. status.HTTP_502_BAD_GATEWAY -> This indicates that the server, while acting as a gateway or proxy, received an invalid response from the upstream server.
    return Response({'error': 'Bad gateway'}, status=status.HTTP_502_BAD_GATEWAY)

4. status.HTTP_503_SERVICE_UNAVAILABLE -> This status is returned when the server is temporarily unable to handle the request. It is commonly used when the server is undergoing maintenance or is overloaded.
    return Response({'error': 'Service unavailable'}, status=status.HTTP_503_SERVICE_UNAVAILABLE)

5. status.HTTP_504_GATEWAY_TIMEOUT -> This indicates that the server, while acting as a gateway or proxy, did not receive a timely response from the upstream server.
    return Response({'error': 'Gateway timeout'}, status=status.HTTP_504_GATEWAY_TIMEOUT)

6. status.HTTP_507_INSUFFICIENT_STORAGE -> This status code indicates that the server is unable to store the representation needed to complete the request.
```