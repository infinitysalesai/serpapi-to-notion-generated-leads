SerpApi to Notion - Generated Leads

This project is an automation workflow built with [n8n](https://n8n.io/) that automatically fetches business leads from Google Maps (via SerpApi) and sends them directly to a Notion database.

It’s designed to streamline lead generation — useful for marketers, researchers, or businesses who want to collect contact details from local search results with zero manual effort.


 🚀 Features

 🔍 Fetch leads from Google Maps using SerpApi
 🧠 Extracts key data fields such as `name`, `email`, `website`, and `phone`
 🧹 Removes duplicate leads before saving
 🗂 Automatically adds data into a Notion database for easy management
 ⚡ Built entirely on n8n, using no custom backend or scripts



 🧩 Workflow Overview

| Step | Node Name              | Description                                         |
| ---- | ---------------------- | --------------------------------------------------- |
| 1    | Manual Trigger     | Starts the workflow manually in n8n                 |
| 2    | Set Query          | Defines the search query (“Hotels in Bonny Island”) |
| 3    | Fetch from SerpApi | Fetches local business results from SerpApi         |
| 4    | Extract Leads      | Extracts relevant fields from the API response      |
| 5    | Remove Duplicates  | Ensures unique business names before saving         |
| 6    | Save to Notion     | Adds each lead into a connected Notion database     |



 🧠 How It Works

1. The workflow triggers manually in n8n.
2. The HTTP Request node calls the SerpApi endpoint:

   ```
   https://serpapi.com/search.json?engine=google_maps&q=Hotels+in+Bonny+Island,+Rivers+State,+Nigeria&type=search&hl=en
   ```
3. Results are processed in the Code node, extracting `title`, `email`, `website`, and `phone`.
4. Duplicates are filtered out.
5. The Notion node saves the leads into your `Generated_Leads` database.



 🔐 Setup Guide

 1. Clone this repo

```bash
git clone https://github.com/<your-username>/serpapi-to-notion-generated-leads.git
cd serpapi-to-notion-generated-leads
```

 2. Import the workflow into n8n

 Open your n8n dashboard → Workflows → Import from File
 Select `workflow.json`

 3. Create API credentials

 SerpApi Key: Get from [https://serpapi.com/manage-api-key](https://serpapi.com/manage-api-key)
 Notion Integration Key:

  1. Go to [https://www.notion.so/my-integrations](https://www.notion.so/my-integrations)
  2. Create a new internal integration
  3. Copy the API key and paste it into n8n credentials

 4. Share the database with your Notion integration

 Open your Notion database
 Click ... (three dots) → Add Connections → Select your Integration

 5. Run your workflow

Click Execute Workflow in n8n — your Notion database will automatically populate with new business leads.



 🧰 Environment Variables (optional)

To keep your keys safe, use environment variables in n8n:

| Variable      | Description                 |
| ------------- | --------------------------- |
| `SERPAPI_KEY` | Your SerpApi API key        |
| `NOTION_KEY`  | Your Notion integration key |



 📊 Example Output (Notion Database)

| Name               | Email                                                         | Website              | Phone             |
| ------------------ | ------------------------------------------------------------- | -------------------- | ----------------- |
| Bonny Island Hotel | [info@bonnyislandhotel.com](mailto:info@bonnyislandhotel.com) | bonnyislandhotel.com | +234 802 123 4567 |



 🧾 License

MIT License © 2025 Daniel Bassey Etop


 🧑‍💻 Author

Daniel Bassey Etop
Digital Marketer & Automation Enthusiast
infinityautomationsai@gmail.com
