## Permissions
Authentication or identification by itself is not usually sufficient to gain access to information or code. For that, the entity requesting access must have authorization.

— Apple Developer Documentation

* Together with authentication and throttling, permissions determine whether a request should be granted or denied access.

* Permission checks are always run at the very start of the view, before any other code is allowed to proceed. Permission checks will typically use the authentication information in the request.user and request.auth properties to determine if the incoming request should be permitted.

* Permissions are used to grant or deny access for different classes of users to different parts of the API.

* allow access to any authenticated user, and deny access to any unauthenticated user. This corresponds to the IsAuthenticated class in REST framework.

* A slightly less strict style of permission would be to allow full access to authenticated users, but allow read-only access to unauthenticated users. This corresponds to the IsAuthenticatedOrReadOnly class in REST framework.

## How permissions are determined
Permissions in REST framework are always defined as a list of permission classes.

Before running the main body of the view each permission in the list is checked. If any permission check fails an exceptions.PermissionDenied or exceptions.NotAuthenticated exception will be raised, and the main body of the view will not run.

When the permissions checks fail either a "403 Forbidden" or a "401 Unauthorized" response will be returned, according to the following rules:

>> The request was successfully authenticated, but permission was denied. — An HTTP 403 Forbidden response will be returned.
The request was not successfully authenticated, and the highest priority authentication class does not use WWW-Authenticate headers. — An HTTP 403 Forbidden response will be returned.
The request was not successfully authenticated, and the highest priority authentication class does use WWW-Authenticate headers. — An HTTP 401 Unauthorized response, with an appropriate WWW-Authenticate header will be returned.

## Third party packages
The following third party packages are also available.

* DRF - Access Policy
The Django REST - Access Policy package provides a way to define complex access rules in declarative policy classes that are attached to view sets or function-based views. The policies are defined in JSON in a format similar to AWS' Identity & Access Management policies.

* Composed Permissions
The Composed Permissions package provides a simple way to define complex and multi-depth (with logic operators) permission objects, using small and reusable components.

* REST Condition
The REST Condition package is another extension for building complex permissions in a simple and convenient way. The extension allows you to combine permissions with logical operators.

* DRY Rest Permissions
The DRY Rest Permissions package provides the ability to define different permissions for individual default and custom actions. This package is made for apps with permissions that are derived from relationships defined in the app's data model. It also supports permission checks being returned to a client app through the API's serializer. Additionally it supports adding permissions to the default and custom list actions to restrict the data they retrieve per user.

* Django Rest Framework Roles
The Django Rest Framework Roles package makes it easier to parameterize your API over multiple types of users.

* Django REST Framework API Key
The Django REST Framework API Key package provides permissions classes, models and helpers to add API key authorization to your API. It can be used to authorize internal or third-party backends and services (i.e. machines) which do not have a user account. API keys are stored securely using Django's password hashing infrastructure, and they can be viewed, edited and revoked at anytime in the Django admin.

* Django Rest Framework Role Filters
The Django Rest Framework Role Filters package provides simple filtering over multiple types of roles.

* Django Rest Framework PSQ
The Django Rest Framework PSQ package is an extension that gives support for having action-based permission_classes, serializer_class, and queryset dependent on permission-based rules.