# Permissions & Postgresql

## DRF Permissions

### Permissions
permissions determine whether a request should be granted or denied access.
Permissions are used to grant or deny access for different classes of users to different parts of the API.

### How permissions are determined

Before running the main body of the view each permission in the list is checked. If any permission check fails an exceptions.PermissionDenied or exceptions.NotAuthenticated exception will be raised, and the main body of the view will not run.

* The request was successfully authenticated, but permission was denied. — An HTTP 403 Forbidden response will be returned.
* The request was not successfully authenticated, and the highest priority authentication class does not use WWW-Authenticate headers. — An HTTP 403 Forbidden response will be returned.
* The request was not successfully authenticated, and the highest priority authentication class does use WWW-Authenticate headers. — An HTTP 401 Unauthorized response, with an appropriate WWW-Authenticate header will be returned.

### Object level permissions
used to determine if a user should be allowed to act on a particular object, which will typically be a model instance.

#### Limitations of object level permissions
Often when you're using object level permissions you'll also want to filter the queryset appropriately, to ensure that users only have visibility onto instances that they are permitted to view.

### Setting the permission policy
default permission policy may be set globally, using the DEFAULT_PERMISSION_CLASSES setting. 
can also set the authentication policy on a per-view, or per-viewset basis, using the APIView class-based views.
```
from rest_framework.permissions import IsAuthenticated
from rest_framework.response import Response
from rest_framework.views import APIView

class ExampleView(APIView):
    permission_classes = [IsAuthenticated]

    def get(self, request, format=None):
        content = {
            'status': 'request was permitted'
        }
        return Response(content)
```
### API Reference
#### 1. AllowAny
#### 2. IsAuthenticated
deny permission to any unauthenticated user
#### 3. IsAdminUser
The IsAdminUser permission class will deny permission to any user, unless user.is_staff is True in which case permission will be allowed.

#### 4. IsAuthenticatedOrReadOnly
#### 5. DjangoModelPermissions
#### 6. DjangoModelPermissionsOrAnonReadOnly
#### 7. DjangoModelPermissionsOrAnonReadOnly
#### 8. DjangoObjectPermissions

### Custom permissions
To implement a custom permission, override BasePermission and implement either, or both, of the following methods:

.has_permission(self, request, view)
.has_object_permission(self, request, view, obj)
The methods should return True if the request should be granted access, and False otherwise.

If you need to test if a request is a read operation or a write operation, you should check the request method against the constant SAFE_METHODS, which is a tuple containing 'GET', 'OPTIONS' and 'HEAD'




