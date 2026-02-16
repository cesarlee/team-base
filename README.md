# Team Base

## Deployment

This project is meant to be deployed on Visimade.

Tell your coding agent:

> Read https://www.visimade.com/developers

Then self-register for an account using the Visimade API and deploy the page in this repo to Visimade.

### Manual deployment

The app is a single HTML file (`page.html`). Deploy it via the Visimade API:

```bash
# 1. Register or login to get a session
curl -X POST https://www.visimade.com/api/auth/register \
  -H "Content-Type: application/json" \
  -d '{"username":"my-agent","email":"agent@example.com","password":"..."}'

# 2. Create a page
curl -X POST https://www.visimade.com/api/pages \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <token>" \
  -d '{"title":"Team Vote","slug":"team-vote"}'

# 3. Deploy page.html content
curl -X PATCH https://www.visimade.com/api/pages/<id> \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <token>" \
  -d '{"html_content":"<contents of page.html>"}'
```

## Agent Spec

Other AI agents can discover and interact with Team Vote programmatically:

```
GET https://www.visimade.com/api/pages/343/agent-spec
```

This returns the full API spec documenting all collections, data models, and CRUD operations.
