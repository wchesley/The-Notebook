# ASP.NET Core
ASP.NET Core is a cross-platform, high-performance, open-source framework for building modern, cloud-enabled, Internet-connected apps.  

## Select list:  
###### [Repo link](https://github.com/wchesley/CIDM-4390-InitialReviewAssignment) 
Recently for a school assignment I used a select list to have users choose a team leader for a team. In doing so I noticed that retreiving the value selected from the list was not as straight forward as I had previously thought. Initially I had thought. Normally you bind the property to get the value from the HTTP Request. However with a select list I ran into the following error:  
`InvalidOperationException: Could not create an instance of type 'Microsoft.AspNetCore.Mvc.Rendering.SelectList'. Model bound complex types must not be abstract or value types and must have a parameterless constructor. Alternatively, set the 'teamLeaders' property to a non-null value in the 'CodingClub.Pages.CreateTeam' constructor.`   
Un-binding the property resolved the error however it didn't retreive the value from the form. For the time being I left my solution as sort of a hack:  
```Csharp
var thing = Request.Form["TeamLeader"];
int.TryParse(thing, out int TLID); 
var newTeamLead = await _context.ClubMember.FirstOrDefaultAsync(tl => tl.MemberID == TLID);
```

This is the old way of getting values from forms in asp.net, but I have not found a good alternative solution as of yet. ref: https://docs.microsoft.com/en-us/previous-versions/iis/6.0-sdk/ms525985(v=vs.90) 