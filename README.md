# GlobalPowerBIAndFabricSummit2024
Extract data from the website of the Global Power BI and Fabric Summit 2024, create a lakehouse inside Microsoft Fabric, create delta tables use Power BI Desktop to connect to the Semantic Model.
The data used is extracted from the Summit website (consent was given by Rezu Rad), nevertheless there is no profesional relationship between radacad and I. Next there is also no other professional relationship between Reza Rad and I. The only relationship that exits is our common interest in sharing knowledge and learning, and being friends.
## The notebooks
Currently the python code is not optimized, as I created while attending the virtual Global Power BI & Microsft Fabric Summit 2024. For this reason, it can be difficult if you have absolutely no experience using notebooks with Microsoft Fabric. I will create a separate document where I explain all the things Pythin in more detail.
### the notebook - globalPowerBISummit2024_getData
This notebook extracts data from the website, and stores this data in a folder, the path to the folder is defined as a variable inside a cell_
+ filePath = "Files/PowerBIAndFabricSummit/2024/"
### the notebook - globalPowerBISummit2024_transformData
This notebook is using three variables
+ filePathTimezones = "Files/PowerBIAndFabricSummit/"
+ filePath = "Files/PowerBIAndFabricSummit/2024/"
+ deltaTablePrefix = "globalSummit_"
The first variable points to a variable that contains timezoneoffsets,it's expected that you manually upload the csv to the folder that defined with the variable.
The second variable is pointing to the folder in the files section extracted from the website.
## The semantic model
Because I have no better idea, on how to share relationships andmeasures I created in the semantic table, I provide these measures as codeblock and the relationships as an image.
### relationships
![Alt text](https://github.com/tomatminceddata/GlobalPowerBIAndFabricSummit2024/blob/main/images/semantic%20model%20relationships%202024-02-13.png)
### measures - hometable: globalSummit_dim_sessions
```
no of sessions = 
DISTINCTCOUNT( 'globalsummit_dim_sessions'[sessionId] )
```
```
sessionDescription (ms) = 
CONCATENATEX(
    CALCULATETABLE( 
        VALUES( 'globalsummit_dim_sessions'[description]  )
        , TREATAS( VALUES( 'globalsummit_fact_schedule'[sessionId] ) , 'globalsummit_dim_sessions'[sessionId] )
    )
    , 'globalsummit_dim_sessions'[description]
)
```
```
sessionTitle (ms) = 
CONCATENATEX(
    CALCULATETABLE( 
        VALUES( 'globalsummit_dim_sessions'[title]  )
        , TREATAS( VALUES( 'globalsummit_fact_schedule'[sessionId] ) , 'globalsummit_dim_sessions'[sessionId] )
    )
    , 'globalsummit_dim_sessions'[title]
)
```
### measures - hometable: globalSummit_dim_speakers
```
no of speakers = DISTINCTCOUNT( 'globalsummit_dim_speakers'[speakerId] )
```
## The report
Current I have some issues with creating a pbit when I'm connected to a semantic model after I converted it to a local model. Until I have this fixed, I can onyl create a screenshot what I have build so far.
![Alt text](https://github.com/tomatminceddata/GlobalPowerBIAndFabricSummit2024/blob/main/images/sampleReport%20with%20tooltippage.png)
