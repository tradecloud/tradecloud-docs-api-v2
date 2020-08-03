# Authorization

In the Tradecloud1 API, almost all endpoints are protected with permission-based checks that ensure that the request is only processed if the authenticated user is authorized to execute this operation.

Below you will find an overview of how these _user identity permissions_ \(in short, _permissions_\) are currently configured in our platform. 

## Scope 

| Scope | Explanation  |
| :--- | :--- |
| Not connected companies | All entities of not connected companies. |
| Connected companies | All entities of connected companies. |
| Your company | All entities within your own company. |
| Your buyer company | All entities within your own buyer company. |
| Your supplier company | All entities within your own supplier company. |
| Not connected users | All entities of not connected users. |
| Connected users | All entities of users linked to a connected company. |
| Your user | All entities within the user's account. |
| Your admin | All admin entities within your own company. |

{% hint style="info" %}
Scopes with both read and write permissions n/a are not shown in the permission tables below 
{% endhint %}

## User Permissions 

### Dashboard

#### Supply Chain Activity

| Scope | Read Permission | Write Permission |
| :--- | :--- | :--- |
| Not connected companies | Not allowed  | n/a |
| Connected companies | Not allowed  | n/a |
| Your company | See all supply chain activity wherein your company is involved | n/a |

{% hint style="info" %}
A company is in the lead during a**n** event that's why users are n/a relating to reading permissions. 
{% endhint %}

####  Order performance metrics

| Scope | Read Permission | Write Permission |
| :--- | :--- | :--- |
| Not connected companies | Not allowed  | n/a |
| Connected companies | Not allowed  | n/a |
| Your company | See all supply chain activity wherein your company is involved | n/a |

### Orders

#### Order \(line\)

<table>
  <thead>
    <tr>
      <th style="text-align:left">Scope</th>
      <th style="text-align:left">Read Permission</th>
      <th style="text-align:left">Write Permission</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Not connected companies</td>
      <td style="text-align:left">Not allowed</td>
      <td style="text-align:left">n/a</td>
    </tr>
    <tr>
      <td style="text-align:left">Connected companies</td>
      <td style="text-align:left">Not allowed</td>
      <td style="text-align:left">n/a</td>
    </tr>
    <tr>
      <td style="text-align:left">Your supplier company</td>
      <td style="text-align:left">See all order (line) fields + download attach documents</td>
      <td style="text-align:left">
        <p></p>
        <p>Execute all &quot;BySupplier&quot; actions (aka commands) + communication
          <br
          />, attach documents &amp; add/change item details</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Your buyer company</td>
      <td style="text-align:left">See all order (line) fields + download attach documents</td>
      <td style="text-align:left">Execute all &quot;ByBuyer&quot; action (aka commands) + communication
        <br
        />&amp; attach documents</td>
    </tr>
  </tbody>
</table>

#### Order \(line\) activity

| Scope | Read Permission | Write Permission |
| :--- | :--- | :--- |
| Not connected companies | Not allowed  | n/a |
| Connected companies | See all activities wherein your company is involved | n/a |
| Your company | See all order \(line\) activities | n/a |
| Your user | See all order \(line\) activities | n/a |

### Tasks

| Scope | Read Permission | Write Permission |
| :--- | :--- | :--- |
| Not connected companies | Not allowed  | n/a |
| Connected companies | Not allowed  | n/a |
| Your company | See all conversation & order tasks	 | Perform all conversation & order tasks |
| Your user | See al conversation & order tasks | Perform all conversation & order tasks |

### My Company

#### Network

| Scope | Read Permission | Write Permission |
| :--- | :--- | :--- |
| Not connected companies | Not allowed  | n/a |
| Connected companies | Not allowed  | n/a |
| Your company | See all connection details | n/a |
| Your admin | See all connection details | Add or update a supplier/buyer account code \(update not yet implemented\)  |

#### Invite a new connection

<table>
  <thead>
    <tr>
      <th style="text-align:left">Scope</th>
      <th style="text-align:left">Read Permission</th>
      <th style="text-align:left">Write Permission</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Connected companies</td>
      <td style="text-align:left">Not allowed</td>
      <td style="text-align:left">n/a</td>
    </tr>
    <tr>
      <td style="text-align:left">Your company</td>
      <td style="text-align:left">Not allowed</td>
      <td style="text-align:left">n/a</td>
    </tr>
    <tr>
      <td style="text-align:left">Not connected users</td>
      <td style="text-align:left">Not allowed</td>
      <td style="text-align:left">n/a</td>
    </tr>
    <tr>
      <td style="text-align:left">Connected users</td>
      <td style="text-align:left">Not allowed</td>
      <td style="text-align:left">n/a</td>
    </tr>
    <tr>
      <td style="text-align:left">Your user</td>
      <td style="text-align:left">
        <p>Find all not connected sellers NAMES + company name(when you are a buyer)
          <br
          />
        </p>
        <p>Find all not connected purchases NAMES (when you are a supplier)
          <br />
        </p>
      </td>
      <td style="text-align:left">send invite</td>
    </tr>
  </tbody>
</table>

#### Validate a new connection

| Scope | Read Permission | Write Permission |
| :--- | :--- | :--- |
| Connected companies | Not allowed  | n/a |
| Your company | Received connection request in the portal | Accept/ Reject offer  |
| Not connected users | not Allowed  | n/a |
| Connected users | Not allowed | n/a |
| Your user | Received e-mail | Accept / Reject offer |

#### Team

| Scope | Read Permission | Write Permission |
| :--- | :--- | :--- |
| Not connected companies | Not allowed  | Not allowed  |
| Connected companies | See all team members and positions \(if filled\) | Not allowed  |
| Your company | See all team members and positions \(if filled\) | Not allowed  |

#### Invite a new user

| Scope | Read Permission | Write Permission |
| :--- | :--- | :--- |
| Your admin  | n/a | Send invitation to anybody |

{% hint style="info" %}
Only admins and super users are allowed to invite new users 
{% endhint %}

#### Validate a new user

| Scope | Read Permission | Write Permission |
| :--- | :--- | :--- |
| Not connected users | Not allowed | Not allowed |
| Connected users | Not allowed | Not allowed |
| Your company | Not allowed | Not allowed |
| Your user | Received e-mail | Create password |

#### Company settings

| Scope | Read Permission | Write Permission |
| :--- | :--- | :--- |
| Not connected companies | Public profile | Not allowed  |
| Connected companies | Public profile  | Not allowed  |
| Your company | See all settings | Not allowed  |
| Your admin | See all settings | Update all settings |

{% hint style="info" %}
Public profile is not yet developed, till then Public profile = Not allowed
{% endhint %}

#### Company activity

| Scope | Read Permission | Write Permission |
| :--- | :--- | :--- |
| Not connected companies | Not allowed  | n/a |
| Connected companies | Not allowed  | n/a  |
| Your company | See all activity | n/a |

### My profile 

#### User settings

| Scope | Read Permission | Write Permission |
| :--- | :--- | :--- |
| Not connected users | Public profile | Not allowed |
| Connected users | Public profile | Not allowed  |
| Your company | All settings except password recovery | Not allowed |
| Your user | All settings | allowed for all settings  |

{% hint style="info" %}
Public profile is not yet developed, till then Public profile = Not allowed 
{% endhint %}

#### User activity

| Scope | Read Permission | Write Permission |
| :--- | :--- | :--- |
| Not connected users | Not allowed  | n/a |
| Connected users | Not allowed  | n/a |
| Your company | See all activity | n/a |
| Your user | See all activity | n/a |

