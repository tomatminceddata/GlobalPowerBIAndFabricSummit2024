# GlobalPowerBIAndFabricSummit2024
Extract data from the website of the Global Power BI Summit and Fabric Summit 2024, create a lakehouse inside Microsoft Fabric, create delta tables use Power BI Desktop to connect to the Semantic Model.
The data used is extracted from the Summit website (consent was given by Rezu Rad), nevertheless there is no profesional relationship between radacad and I. Next there is also no other professional relationship between Reza Rad and I. The only relationship that exits is our common interest in sharing knowledge and learning, and being friends.
## The notebooks
Currently the python code is not optimized, as I created while attending the virtual Global Power BI & Microsft Fabric Summit 2024. For this reason, it can be difficult if you have absolutely no experience using notebooks with Microsoft Fabric. I will create a separate document where I explain all the things Pythin in more detail.
### the notebook - globalPowerBISummit2024_getData
This notebook extracts data from the website, and stores this data in a folder, the path to the folder is defined as a variable inside a cell_
filePath = "Files/PowerBIAndFabricSummit/2024/"

