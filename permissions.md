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

| Description | Scope | Role | Read Permission | Write Permission |
| :--- | :--- | :--- | :--- | :--- |
| Supply Chain Activity | Company | n/a | See all activities | n/a |
| Order performance metrics | Company | n/a | See all Order performance metrics | n/a |

#### Orders

| Description | Scope | Role | Read Permission | Write Permission |
| :--- | :--- | :--- | :--- | :--- |
| Order \(line\) | Company | Buyer | See all order \(line\) fields | Execute all "ByBuyer" action \(aka commands\) |
| Order \(line\) | Company | Supplier | See all order \(line\) fields | Execute all "BySupplier" actions \(aka commands\) |
| Order \(line\) activity | Company | n/a | See all order \(line\) activities | n/a |
| Order \(line\) conversations | Company | n/a | See all order \(line\) conversation messages | Create message |
| Order \(line\) tasks | Company | n/a | See all order \(line\) tasks | Execute all tasks |

#### My Company

<table>
  <thead>
    <tr>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Scope</th>
      <th style="text-align:left">Read Permission</th>
      <th style="text-align:left">Write Permission</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Connection details</td>
      <td style="text-align:left">Company</td>
      <td style="text-align:left">See all connected companies</td>
      <td style="text-align:left">Not allowed</td>
    </tr>
    <tr>
      <td style="text-align:left">Invite a new connection</td>
      <td style="text-align:left">Platform</td>
      <td style="text-align:left">Find any user (limited fields)</td>
      <td style="text-align:left">n/a</td>
    </tr>
    <tr>
      <td style="text-align:left">Validate a new connection</td>
      <td style="text-align:left">n/a</td>
      <td style="text-align:left">Received e-mail</td>
      <td style="text-align:left">
        <p>Request link</p>
        <p>(with Validation token?)</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Team</td>
      <td style="text-align:left">Company</td>
      <td style="text-align:left">See all team members</td>
      <td style="text-align:left">Not allowed</td>
    </tr>
    <tr>
      <td style="text-align:left">Invite a new user</td>
      <td style="text-align:left">Company</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">Invite any user</td>
    </tr>
    <tr>
      <td style="text-align:left">Validate a new user</td>
      <td style="text-align:left">n/a</td>
      <td style="text-align:left">Received e-mail</td>
      <td style="text-align:left">Validation token</td>
    </tr>
    <tr>
      <td style="text-align:left">Settings</td>
      <td style="text-align:left">Company</td>
      <td style="text-align:left">Not allowed</td>
      <td style="text-align:left">Not allowed</td>
    </tr>
    <tr>
      <td style="text-align:left">Activity</td>
      <td style="text-align:left">Company</td>
      <td style="text-align:left">See all activities</td>
      <td style="text-align:left">n/a</td>
    </tr>
  </tbody>
</table>

#### My Profile

| Description | Scope | Read Permission | Write Permission |
| :--- | :--- | :--- | :--- |
| View User Profile | Platform \(?\) | TODO | TODO |
| Update User Profile | User | TODO | TODO |

## Admin Permissions

Permissions in addition to above User permissions.

TODO - Provide permission tables just like the ones above with data for Admin users

amend account code 

#### My Company

<table>
  <thead>
    <tr>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Scope</th>
      <th style="text-align:left">Read Permission</th>
      <th style="text-align:left">Write Permission</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Connection details</td>
      <td style="text-align:left">Company</td>
      <td style="text-align:left">See all connected companies</td>
      <td style="text-align:left">Not allowed</td>
    </tr>
    <tr>
      <td style="text-align:left">Invite a new connection</td>
      <td style="text-align:left">Platform</td>
      <td style="text-align:left">Find any user (limited fields)</td>
      <td style="text-align:left">n/a</td>
    </tr>
    <tr>
      <td style="text-align:left">Validate a new connection</td>
      <td style="text-align:left">n/a</td>
      <td style="text-align:left">Received e-mail</td>
      <td style="text-align:left">
        <p>Request link</p>
        <p>(with Validation token?)</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Team</td>
      <td style="text-align:left">Company</td>
      <td style="text-align:left">See all team members</td>
      <td style="text-align:left">Not allowed</td>
    </tr>
    <tr>
      <td style="text-align:left">Invite a new user</td>
      <td style="text-align:left">Company</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">Invite any user</td>
    </tr>
    <tr>
      <td style="text-align:left">Validate a new user</td>
      <td style="text-align:left">n/a</td>
      <td style="text-align:left">Received e-mail</td>
      <td style="text-align:left">Validation token</td>
    </tr>
    <tr>
      <td style="text-align:left">Settings</td>
      <td style="text-align:left">Company</td>
      <td style="text-align:left">Not allowed</td>
      <td style="text-align:left">Not allowed</td>
    </tr>
    <tr>
      <td style="text-align:left">Activity</td>
      <td style="text-align:left">Company</td>
      <td style="text-align:left">See all activities</td>
      <td style="text-align:left">n/a</td>
    </tr>
  </tbody>
</table>

## Superuser Permissions

Superuser only permissions \(A superuser does NOT have above User permissions\)

TODO - Provide permission tables just like the ones above with data for Superuser users

create connection \(API only\)

create user \(API only\)

create company \(API only\)

<table>
  <thead>
    <tr>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Scope</th>
      <th style="text-align:left">Read Permission</th>
      <th style="text-align:left">Write Permission</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">bla/td>
      <td style="text-align:left">bla</td>
      <td style="text-align:left">bla</td>
      <td style="text-align:left">bla</td>
    </tr>
  </tbody>
</table>
