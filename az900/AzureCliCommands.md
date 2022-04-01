# List of Azure cli commands 

##### For Resource Group

   ```powershell
    # Azure login and version of cli 
   
      az --version
      az login //Prompt will open browser to provide user id and password of azure account 

   # Command to create resource group

      az group create --name ProgramFiction ResourceGroup --location southindia
   
   # Command to see resource groups in your subscription
     
      az group list
   
   # Show one group
   
      az group show --name ProgramFictionGroup
   
   # Delete Resource group

      az group delete --name ProgramFictionGroup

   # Deploy Resource Group

      az storage account create --resource-group ProgramFictionGroup --name ProgramFictionstore --location southindia --sku Standard_LRS --kind StorageV2
   
   # To deploy an ARM template or Bicep file

      az deployment group create --resource-group ProgramFictionGroup --template-file storage.bicep
   
   # Show Resources as a list

      az --resource list -- resource-group programfiction -- out table

   # Show results with specific column 

      az resource list - resource-group programfiction --out table --query "[].{Name:name, Type:type}"
   # Create service plan 

      az appservice plan create --resource-group progamfiction --name TestAppSvcPlan --sku S1

   # Create azure website 

      az webapp create --resource-group programfiction --plan TestAppSvcPlan --name programfictiontestapp

   # Create Azure VM

      az vm create \
            --resource-group myResourceGroup \
            --name myVM \
            --image Win2019Datacenter \
            --public-ip-sku Standard \
            --admin-username azureuser 
    # Open port for web traffic

      az vm open-port --port 80 --resource-group myResourceGroup --name myVM
      
   ```
