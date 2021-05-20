# GitHub Action - Set Variables
Are you missing the Azure DevOps Library variable groups in GitHub Actions?
If yes, then this action will act as a substitution of Library variable groups in GitHub. [Currently only supports windows and ubuntu agents]

This is a GitHub Action used to convert variables.json files into environment variables.

## 1. Add your variable files as json in this folder - .github/variables/{variable_file_name}.json
The format of the file should be:
```
{
  "variables": [
    {
      "name": "variable1",
      "value": "variable1value"
    },
    {
      "name": "variable2",
      "value": "variable2value"
    }
  ]
}
```

## 2. Now in your job, to use these variables, add the following action into your job
```
- name: Set Variable
  uses: deep-mm/set-variables@v1.0
  with:
    # Name of variable file
    variableFileName: 'variables' #Dont write .json here
```
The variables in your variables.json file will now be converted to environment variables that you can use in the next steps of the same job.
Ths scope of variables is only the job and not the entire workflow.

## 3. Use these variables in next steps
```
${{ env.variable1 }}
${{ env.variable2 }}
```
