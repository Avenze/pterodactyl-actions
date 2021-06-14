# pterodactyl-actions
GitHub Action for deploying the repository to a Pterodactyl server using the built in Wings API

# Usage
Create a workflow using this template, apparently the standard one does not work.

```yml
name: Pterodactyl CD Actions

on:
  push:
    branches: [ master ]
  pull_request:
    branches: [ master ]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - name: PterodactylCD
      uses: Avenze/pterodactyl-actions@v1
      with: 
        panel: https://pterodactyl.example.com/
        api_key: ${{ secrets.PANEL_KEY }} # 
        server: ${{ secrets.SERVER_UUID }}
        path: ./home/runner/work/dashboard_backend/dashboard_backend/index.js
        directory: ""
```

The parameters require the following:
- Panel: The URL of your Pterodactyl panel in this format: 'https://pterodactyl.example.com/', do not forget the slash at the end.
- Api Key: This is a client token, not an API Token, here's a guide on how to get a client token:
  ![image](https://user-images.githubusercontent.com/38162785/121948480-94f70e80-cd57-11eb-87e4-2e374ff66cd9.png)
  ![image](https://user-images.githubusercontent.com/38162785/121948528-a3452a80-cd57-11eb-90fd-d51b73911d08.png)
  ![image](https://user-images.githubusercontent.com/38162785/121948650-ca036100-cd57-11eb-93e3-d366d566886f.png)
  Enter whatever you'd like in the Description field, and then press Create, copy the token and paste it into the api_key parameter field.
- Server: You'll need to get the first segment of the servers UUID, here's how:
  ![image](https://user-images.githubusercontent.com/38162785/121949325-9f65d800-cd58-11eb-8897-c77e73192305.png)
  Select the server you'd like to get the UUID from, I'll use this one as an example.
  ![image](https://user-images.githubusercontent.com/38162785/121949419-b73d5c00-cd58-11eb-8164-8252cae799ae.png)
  Go to the settings tab of the server.
  ![image](https://user-images.githubusercontent.com/38162785/121949590-ebb11800-cd58-11eb-8ba1-dbeb4b627afb.png)
  The part I highlited under the Debug Information panel, is what you'll need to add into the server parameter field.
- Path: I'm still trying to figure this one out, I'll update this later when I get a response from the original developer.
- Directory: Same goes for this one, I'm unsure about this, I'll update later.

# Credits
- ForgottenWorld: Owners of the original repository (https://github.com/ForgottenWorld)
- Avenze: Documentation improvement (https://github.com/Avenze)
