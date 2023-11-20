```mermaid
sequenceDiagram
  participant User
  participant ZammadAPI
  participant EmailService

  User->>ZammadAPI: GET /api/v1/users/me
  ZammadAPI->>User: User Information

  User->>ZammadAPI: POST /api/v1/signin
  ZammadAPI->>User: {"token": "your_access_token", "expires_at": "expiration_timestamp"}

  User->>ZammadAPI: POST /api/v1/forgot_password
  ZammadAPI->>EmailService: Send reset instructions
  EmailService-->>User: Password reset instructions sent to your email.
```

## Authentication

Both the Login and Forgot Password endpoints require authentication. The current user can access their information through a GET request to the `/api/v1/users/me` endpoint.

Current User > Web

`#{user.web}`

`https://zammad.org` or empty if not set

Current User > VIP

`#{user.vip}`

`false` or `true`

Current User > Updated by > Web

`#{user.updated_by.web}`

`https://zammad.org` or empty if not set

Current User > Updated by > VIP

`#{user.updated_by.vip}`

`false` or `true`

Current User > Updated by > Phone

`#{user.updated_by.phone}`

`004930123456789` or empty if not set

Current User > Updated by > Note

`#{user.updated_by.note}`

`Some note to this user` or empty if not set

Current User > Updated by > Mobile

`#{user.updated_by.mobile}`

`0049176123456789` or empty if not set

Current User > Updated by > Login

`#{user.updated_by.login}`

`jdoe`

Current User > Updated by > Lastname

`#{user.updated_by.lastname}`

`Doe` or empty if not set

Current User > Updated by > Firstname

`#{user.updated_by.firstname}`

`John` or empty if not set

Current User > Updated by > Fax

`#{user.updated_by.fax}`

`004930123464789` or empty if not set

Current User > Updated by > Email

`#{user.updated_by.email}`

`jdoe@customer.tld`

Current User > Updated by > Department

`#{user.updated_by.department}`

`Sales` or empty if not set

Current User > Updated by > Address

`#{user.updated_by.address}`

`Some street 1, 12345 Berlin` or empty if not set

Current User > Updated at

`#{user.updated_at}`

`2019-10-07 16:25:00 UTC`

Current User > Phone

`#{user.phone}`

`004930123456789` or empty if not set

Current User > Organization > Shared organization

`#{user.organization.shared}`

`true` or `false`

Current User > Organization > Note

`#{user.organization.note}`

`A note to the organization of the user` or empty if not set

Current User > Organization > Name

`#{user.organization.name}`

Current User > Organization > Domain based assignment

`#{user.organization.domain_assignment}`

Current User > Organization > Domain

`#{user.organization.domain}`

`Zammad GmbH` or empty if not set

Current User > Organization > VIP

`#{user.organization.vip}`

`true` or `false`

Current User > Note

`#{user.note}`

`Some note to this user` or empty if not set

Current User > Mobile

`#{user.mobile}`

`0049176123456789` or empty if not set

Current User > Login

`#{user.login}`

`jdoe`

Current User > Lastname

`#{user.lastname}`

`Doe` or empty if not set

Current User > Firstname

`#{user.firstname}`

`John` or empty if not set

Current User > Fax

`#{user.fax}`

`004930123464789` or empty if not set

Current User > Email

`#{user.email}`

`jdoe@customer.tld`

Current User > Department

`#{user.department}`

`Sales` or empty if not set

Current User > Created by > Web

`#{user.created_by.web}`

`https://zammad.org` or empty if not set

Current User > Created by > VIP

`#{user.created_by.vip}`

`true` or `false`

Current User > Created by > Phone

`#{user.created_by.phone}`

`004930123456789` or empty if not set

Current User > Created by > Note

`#{user.created_by.note}`

`Some note to this user` or empty if not set

Current User > Created by > Mobile

`#{user.created_by.mobile}`

`0049176123456789` or empty if not set

Current User > Created by > Login

`#{user.created_by.login}`

`jdoe`

Current User > Created by > Lastname

`#{user.created_by.lastname}`

`Doe` or empty if not set

Current User > Created by > Firstname

`#{user.created_by.firstname}`

`John` or empty if not set

Current User > Created by > Fax

`#{user.created_by.fax}`

`004930123464789` or empty if not set

Current User > Created by > Email

`#{user.created_by.email}`

`jdoe@customer.tld`

Current User > Created by > Department

`#{user.created_by.department}`

`Sales` or empty if not set

Current User > Created by > Address

`#{user.created_by.address}`

`Some street 1, 12345 Berlin` or empty if not set

Current User > Created at

`#{user.created_at}`

`2019-10-07 16:25:00 UTC`

Current User > Address

`#{user.address}`

`Some street 1, 12345 Berlin` or empty if not set

**Note:** The provided samples were provided with admin and ticket.agent permissions. Some attributes/information may not be available in specific situations. Refer to the [Permission Guide](https://docs.zammad.org/en/latest/api/user.html) for more insights.

* [Login](https://tw-elements.com/docs/react/forms/login-form): CSS for user login.
* [Forgot Password](https://tailwindcomponents.com/component/sb-admin-2-forgot-password-page-1): CSS for initiating a password reset.

* * *

```mermaid
graph TD
  subgraph "Zammad API"
    subgraph "Ticket Management"
      subgraph "Tickets API"
        A["Retrieve Ticket Details"]
      end
    end

    subgraph "Ticket Groups and Enrollment"
      B["Automatic Group Creation"]
      C["Step-by-step UI Page"]
      D["Ticket Content Updates"]
    end

    subgraph "UI Steps and Dashboard Access"
      E["Steps Page Display"]
      F["Progress through Steps"]
      G["Ticket Group Closed"]
      H["Direct Access to Dashboard"]
    end

    subgraph "Permissions"
      I["Check Permissions"]
      J["ticket.agent or ticket.customer"]
    end
  end

  subgraph "Additional UI Components"
    K["Steps with Directions Component"]
  end

  A --> B
  B --> C
  C --> D
  D --> E
  E --> F
  F --> G
  G --> H
  I --> J
  C --> K
```

## Ticket Management

Zammad provides a comprehensive API for managing tickets, including details retrieval for an already initiated process. The relevant endpoint is:

* [Tickets API](https://docs.zammad.org/en/latest/api/ticket/index.html?highlight=tickets): Endpoint for interacting with tickets.

For detailed information and additional endpoints, please refer to the [official documentation](https://user-docs.zammad.org/en/latest/basics/what-is-a-ticket.html#).

## Ticket Groups and Enrollment

Zammad automatically creates groups for new users during the enrollment process. The enrollment involves several tracked steps, and the progress is monitored through tickets associated with these groups. The user interface (UI) displays a step-by-step page showcasing ticket content related to each step.

### Retrieve Ticket Details

To obtain information about a specific ticket, the following endpoint can be used:

#### GET /api/v1/tickets/{ticket id}

##### Request

```bash
curl -X GET https://your-zammad-instance/api/v1/tickets/{ticket_id} \
  -H "Authorization: Bearer your_access_token"
```

##### Response

```json
HTTP/1.1 200 OK

{
   "id": 3,
   "group_id": 1,
   "priority_id": 2,
   "state_id": 4,
   "organization_id": 3,
   "number": "22003",
   "title": "Order 787556",
   "owner_id": 3,
   "customer_id": 7,
   "note": null,
   "first_response_at": null,
   "first_response_escalation_at": null,
   "first_response_in_min": null,
   "first_response_diff_in_min": null,
   "close_at": null,
   "close_escalation_at": null,
   "close_in_min": null,
   "close_diff_in_min": null,
   "update_escalation_at": null,
   "update_in_min": null,
   "update_diff_in_min": null,
   "last_contact_at": "2021-06-03T09:57:17.987Z",
   "last_contact_agent_at": "2021-06-03T09:57:17.987Z",
   "last_contact_customer_at": "2021-06-01T11:57:17.935Z",
   "last_owner_update_at": null,
   "create_article_type_id": 1,
   "create_article_sender_id": 2,
   "article_count": 2,
   "escalation_at": null,
   "pending_time": null,
   "type": null,
   "time_unit": null,
   "preferences": {},
   "updated_by_id": 4,
   "created_by_id": 7,
   "created_at": "2021-06-01T11:57:17.935Z",
   "updated_at": "2021-11-03T11:57:17.997Z"
}
```

### UI Steps and Dashboard Access

The UI presents a step-by-step page that guides users through the enrollment process. Each step corresponds to a tracked ticket associated with the created group. The ticket content is dynamically updated as users progress through each step.

**Important:** The steps page remains visible until all required steps are completed. Once the associated ticket group is marked as closed, users gain direct access to the dashboard.

## Permissions

To access ticket details, users need the appropriate permissions:

* `ticket.agent` or `ticket.customer`

Ensure the provided access token has the necessary permissions for the requests. For further insights into permissions, please refer to the [Permission Guide](https://docs.zammad.org/en/latest/api/ticket/index.html?highlight=tickets).

## Additional UI Components

Library used but it has been reworked. [Steps with Directions](https://tailwindcomponents.com/component/steps-with-directions) component visually represent the enrollment process.

* * *

```mermaid
graph TD
  subgraph "Zammad Knowledge Base API"
    A[Retrieve KB Article]
    B[Schema Issue]
    C[Resolution]
    D[Steps to Use]
    A -->|HTTP GET| B
    B -->|Add kb_locale_id attribute| C
    C --> D
  end

  subgraph "ContentLayer Implementation"
    E[Remote Files Source]
    F[Example Implementation]
    G[ContentLayer Documentation]
  end

  subgraph "Implementation Flow"
    H[Zammad Provides KB API]
    I[ContentLayer Loads KB Info]
    J[Users Log In]
    K[ContentLayer Fetches Synced Content]
    L[Changes Occur?]
    M[ContentLayer Updates Content]
    N[No Changes]
  end

  A -->|Error Response| B
  B -->|Add Attribute| C
  C -->|Updated Request| D
  E -->|Syncs Content| F
  F -->|Uses Git Repository| G
  H -->|Retrieves Article Details| I
  I -->|Handles Caching| J
  J -->|Fetches Synced KB Content| K
  K -->|Yes| L
  L -->|Yes| M
  M -->|No| N
  N -->|End| K
```
### Zammad Knowledge Base API

#### Retrieve KB Article

* **Schema Issue:** The provided error indicates a missing attribute in the schema: "Translations kb locale must exist."
* **Resolution:** Add the `kb_locale_id` attribute inside the `translations_attributes`. The specified locale must be created on the server beforehand.

#### Steps to Use:

```bash
curl --location --request POST 'https://your-zammad-instance/api/v1/knowledge_bases/1/answers' \
--header 'Authorization: Token token=_____' \
--header 'Content-Type: application/json' \
--data-raw '{"category_id":"1","translations_attributes":[{"title":"test05 api", "id":"","content_attributes":{"body":"test05 api body"},"kb_locale_id": "your_locale_id"}]}'
```

* Ensure to replace `"your_locale_id"` with the actual locale ID created on the server.

[Zammad Documentation Link](https://community.zammad.org/t/solved-knowledge-base-api-create-article/9127)

### ContentLayer Implementation

#### Remote Files Source

ContentLayer facilitates the synchronization of content files from remote sources. The provided example demonstrates the usage of a remote Git repository.

##### Example Implementation:

```javascript
import { defineDocumentType } from '@contentlayer/source-files'
import { makeSource } from '@contentlayer/source-remote-files'

const Post = defineDocumentType(() => ({
  name: 'Post',
  filePathPattern: `docs/**/*.md`,
  fields: {
    title: { type: 'string', required: false },
    // ... (other fields)
  },
}))

const syncContentFromGit = async (contentDir: string) => {
  const syncRun = async () => {
    const gitUrl = 'https://github.com/vercel/next.js.git'
    // TODO: git pull or git clone (see full example for working code)
  }

  let wasCancelled = false
  let syncInterval

  const syncLoop = async () => {
    await syncRun()

    if (wasCancelled) return

    syncInterval = setTimeout(syncLoop, 1000 * 60)
  }

  // Block until the first sync is done
  await syncLoop()

  return () => {
    wasCancelled = true
    clearTimeout(syncInterval)
  }
}

export default makeSource({
  syncFiles: syncContentFromGit,
  contentDirPath: 'nextjs-repo',
  contentDirInclude: ['docs'],
  documentTypes: [Post],
  disableImportAliasWarning: true,
})
```

#### ContentLayer Documentation

For detailed information on ContentLayer's remote files source, visit the [ContentLayer Remote Files Documentation](https://contentlayer.dev/docs/sources/remote-files-fbb47906).

### Implementation Flow

1. Zammad provides the KB API for retrieving article details.
2. ContentLayer loads information from Zammad's KB, handling caching.
3. Users log in, and ContentLayer fetches information from the synced KB content.
4. If changes occur, ContentLayer updates by dropping and refetching all content.
5. If no changes, nothing is fetched.

This implementation ensures seamless integration between Zammad's KB API and ContentLayer for efficient content retrieval and delivery.

* * *
