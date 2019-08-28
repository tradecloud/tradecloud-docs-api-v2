# Permissions

In the Tradecloud1 API, almost all endpoints are protected with permission-based checks that ensure that the request is only processed if the authenticated user is authorized to execute this operation.

Below you will find an overview of how these _user identity permissions_ \(in short, _permissions_\) are currently configured in our platform.

## Scopes

TODO: explanation of scopes

| Scope | Explanation |
| :--- | :--- |
| Platform | All entities within the Tradecloud1 platform \(across companies\). |
| Company | All entities within your company. |
| User | All entities within the user's account. |

## User Permissions

#### Dashboard

| Description | Scope | Read Permission | Write Permission |
| :--- | :--- | :--- | :--- |
| Supply Chain Activity | Company | See all activities | - |
| Order performance metrics | Company | See all Order performance metrics | - |

#### Orders

| Description | Scope | Read Permission | Write Permission |
| :--- | :--- | :--- | :--- |
| Order \(line\) details | Company | See all order \(line\) details | TODO |
| Order \(line\) activity | Company | See all order \(line\) activities | TODO |
| Order \(line\) conversations | Company | See all order \(line\) conversation messages | TODO |
| Order \(line\) tasks | Company | See all order \(line\) tasks | TODO |

#### My Company

| Description | Scope | Read Permission | Write Permission |
| :--- | :--- | :--- | :--- |
| Connection details | Company | TODO - See all connected companies | TODO \(verify\) |
| Create a new connection | Platform | TODO + scope | TODO + scope |
| Team | Company | TODO | TODO - investigate |
| Settings | Company | TOOD | TODO |
| Activity | Company | See [Dashboard](permissions.md#dashboard) | See [Dashboard](permissions.md#dashboard) |

#### My Profile

| Description | Scope | Read Permission | Write Permission |
| :--- | :--- | :--- | :--- |
| View User Profile | Platform \(?\) | TODO | TODO |
| Update User Profile | User | TODO | TODO |

## Admin Permissions

TODO - Provide permission tables just like the ones above with data for Admin users

## Superuser Permissions

TODO - Provide permission tables just like the ones above with data for Superuser users

