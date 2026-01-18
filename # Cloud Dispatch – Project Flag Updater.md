# Cloud Dispatch – Project Flag Updater

This is a lightweight, static web app designed to interact with the **Command Alkon Cloud Dispatch API**. It allows users to:

- Authenticate using API credentials
- Fetch all active projects
- Filter projects that lack `restrictedVehicleTypeRefs`
- Update the `restrictedVehicleTypeRefs` field for all or individual projects

## 🔐 Authentication

To authenticate, enter the following credentials:

- **Entity Reference**
- **API Key**
- **Client ID**
- **Client Secret**
- **API Scope Ref**

Click **"Generate Access Token"** to retrieve a bearer token via:

- `POST /api/login`
- `GET /api/tokens/refresh-access-token`

## 🔍 Project Management Features

### 1. Fetch Active Projects

- Button: **Fetch Active Projects**
- Calls: `GET /v4/services/setup/{entityRef}/projects`
- Filters on `status === "ACTIVE"`

### 2. Fetch Projects With No Vehicle Type

- Button: **Fetch Projects with No Vehicle Type**
- Same call as above
- Additional filter: projects where `restrictedVehicleTypeRefs` is empty or undefined

### 3. Update Single Project

- Each row has an **"Update"** button
- Uses `PATCH /projects/{crn}`
- Sends:

```json
{
  "restrictedVehicleTypeRefs": ["cffe3344-b334-59ee-8ba4-abaf0325a1eb"]
}
```

### 4. Update ALL Projects

- Button: **Update ALL Projects**
- Loops over currently displayed rows
- Uses `PATCH` per project with same payload

## 🧪 Technologies

- Pure HTML/CSS/JavaScript
- No build tools or frameworks
- Works offline once loaded

## 🚀 Deployment

Drag-and-drop to [Netlify Drop](https://app.netlify.com/drop) or serve via any static host.

## ✅ Status

✅ Fully working as of latest update

- UI: Sidebar + Table Layout
- Supports PATCH and PUT logic
- Handles filtered updates

---

Feel free to clone and customize for additional API integrations (e.g., Products, Orders, Drivers).
