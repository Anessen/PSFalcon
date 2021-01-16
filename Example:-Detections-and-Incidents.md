Detections and Incidents
API reference
Find incidents
Get-FalconIncident [-Detailed]
Show CrowdScores
Get-FalconScore
Update the status of multiple incidents
Invoke-FalconIncidentAction -Name update_status -Value in_progress -Ids <id>, <id>

NOTE: Corresponding detections can be updated with the -UpdateDetects and -OverwriteDetects parameters, using a value of $true.
Find behaviors
Get-FalconBehavior [-Detailed]
Find detections
Get-FalconDetection -Filter "status:'new'+first_behavior:>'2020-01-01'" -Sort first_behavior.desc [-Detailed]
Modify the status of multiple detections
Edit-FalconDetection -Ids <id>, <id> -Status new
Hide detections from the UI
WARNING: Hiding detections is not reversible!
Edit-FalconDetection -Ids <id>, <id> -ShowInUi $false