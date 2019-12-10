# Authorization

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

### Dashboard

| Description | Scope | Role | Read Permission | Write Permission |
| :--- | :--- | :--- | :--- | :--- |
| Supply Chain Activity | Company | n/a | See all activities | n/a |
| Order performance metrics | Company | n/a | See all Order performance metrics | n/a |

### Orders

| Description | Scope | Role | Read Permission | Write Permission |
| :--- | :--- | :--- | :--- | :--- |
| Order \(line\) | Company | Buyer | See all order \(line\) fields | Execute all "ByBuyer" action \(aka commands\) |
| Order \(line\) | Company | Supplier | See all order \(line\) fields | Execute all "BySupplier" actions \(aka commands\) |
| Order \(line\) activity | Company | n/a | See all order \(line\) activities | n/a |
| Order \(line\) conversations | Company | n/a | See all order \(line\) conversation messages | Create message |
| Order \(line\) tasks | Company | n/a | See all order \(line\) tasks | Execute all tasks |

### My Company

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
      <td style="text-align:left">Not allowed</td>
      <td style="text-align:left">Not allowed</td>
    </tr>
    <tr>
      <td style="text-align:left">Validate a new user</td>
      <td style="text-align:left">n/a</td>
      <td style="text-align:left">Not allowed</td>
      <td style="text-align:left">Not allowed</td>
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
</table>\#\#\# My Profile

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
      <td style="text-align:left">User Profile</td>
      <td style="text-align:left">Platform</td>
      <td style="text-align:left">View any user profile (limited fields)</td>
      <td style="text-align:left">Not allowed</td>
    </tr>
    <tr>
      <td style="text-align:left">User Profile</td>
      <td style="text-align:left">User</td>
      <td style="text-align:left">View own profile</td>
      <td style="text-align:left">
        <p>Update all fields</p>
        <p>Change password</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">User profile</td>
      <td style="text-align:left">Company</td>
      <td style="text-align:left">View co-workers profile</td>
      <td style="text-align:left">Not allowed</td>
    </tr>
  </tbody>
</table>\#\# Admin Permissions Permissions in addition to above User permissions. \#\#\# My Company \| Description \| Scope \| Read Permission \| Write Permission \| \| :--- \| :--- \| :--- \| :--- \| \| Connection details \| Company \| n/a \| Update account code \| \| Invite a new user \| Company \| n/a \| Invite any user \| \| Validate a new user \| n/a \| Received e-mail \| Validation token \| \| Settings \| Company \| See all fields \| Update all fields \| \#\# Superuser Permissions Superuser only permissions \\(A superuser does NOT have above User permissions\\)

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
      <td style="text-align:left">Impersonate company</td>
      <td style="text-align:left">Platform</td>
      <td style="text-align:left">Everything</td>
      <td style="text-align:left">
        <p>Invite user</p>
        <p>Invite connection</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Create company</td>
      <td style="text-align:left">Platform</td>
      <td style="text-align:left">n/a</td>
      <td style="text-align:left">Allowed</td>
    </tr>
    <tr>
      <td style="text-align:left">Create connection w/o invite (API only)</td>
      <td style="text-align:left">Platform</td>
      <td style="text-align:left">n/a</td>
      <td style="text-align:left">Allowed</td>
    </tr>
    <tr>
      <td style="text-align:left">Create user w/o invite (API only)</td>
      <td style="text-align:left">Platform</td>
      <td style="text-align:left">n/a</td>
      <td style="text-align:left">Allowed</td>
    </tr>
  </tbody>
</table>