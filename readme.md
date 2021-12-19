# Notion Github Catalog

This action will scan all of the Github repositories available to the provided token and update their information in the specified Notion database.

## Notion integration and token

First, you need to have an integration access token - which you can get from https://www.notion.so/my-integrations after creating an integration.  Give the integration a friendly name like 'Github Actions'.

By default integrations cant access any contentm so you you *must* share your database with the integration you created earlier to be able to access it!

## Notion Database

This action expects a Notion database with the following properties:

  - Name: text
  - URL: url
  - Segment: select
  - Team: select
  - Tags: multi_select
  - Updated: date

It looks like this after it has run:

<img width="1451" alt="Screenshot 2021-12-19 at 12 55 39" src="https://user-images.githubusercontent.com/239305/146673989-01187d53-d2fd-42ba-9968-31442b8cc92d.png">

## Usage

Typically this is used with a changelog builder:

```yaml

- name: Notion github catalog     
  uses: infinitaslearning/notion-github-catalog@main        
  with:          
    github_owner: infinitaslearning
    github_token: ${{ secrets.GITHUB_TOKEN }}
    notion_token: ${{ secrets.NOTION_TOKEN }}
    database: 619f0845c68a4c18837ebdb9812b90c0    
    repository_type: all
```

To get the database ID, simply browse to it, click on the '...' and get a 'Copy link'.  The GUID at the end of the URL is the id.

## Development

Assumes you have `@vercel/ncc` installed globally.
After changes ensure you `npm run build`, commit and then submit a PR.
