# SOCRadar-Azure Sentinel Bidirectional Integration

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FRadargoger%2Fazure-sentinel-bidirectional%2Fmain%2Fsocradar-sentinel-integration-arm.json)

When you close an incident in Sentinel, this Logic App updates the alarm status in SOCRadar.

## How It Works

- Polls Sentinel every 5 minutes
- Finds closed incidents with title `SOCRadar-AlarmID-*`
- Updates SOCRadar alarm to RESOLVED

## Deployment

1. Click **Deploy to Azure**
2. Fill parameters:
   - **WorkspaceName**: Your Log Analytics workspace name
   - **SocradarApiKey**: Your SOCRadar API key
   - **CompanyId**: Your SOCRadar company ID
3. After deployment, authorize the API connection

## Post-Deployment

1. Go to Resource Group → `azuremonitorlogs-connection`
2. Click "Edit API connection"
3. Click "Authorize" → Login → Save

## Test

1. Create incident with title `SOCRadar-AlarmID-12345`
2. Close the incident
3. Wait 5 minutes
4. Check SOCRadar - alarm should be RESOLVED
