@startuml
title Activity Diagram: Search & Filter Tools

start

partition "User" {
:Navigates to AI Tools listing page;
:Enters search term and submits;
}

partition "System" {
:Displays tools matching search term;
}

partition "User" {
:Applies filters (category, rating, etc.);
}

partition "System" {
if (Search and Filter Combination) is (Valid and has results) then
:Updates displayed list with filtered results;
:Reflects active filters;
else (No results found)
:Displays "no results" message;
:Suggests popular categories / Clear filters option;
stop
endif
}

partition "User" {
:Expands a tool entry to view extended information;
:Clicks tool's external link;
}

partition "System" {
if (External Link) is (Available) then
:Opens AI tool's external page in new tab;
else (Unavailable)
:Shows error notice and logs failure;
stop
endif
}

partition "User" {
if (Wants to Reset View) is (Yes) then
:Clears search input / Resets filters;
repeat
:Navigates to AI Tools listing page;
repeat while (Wants to search/filter again) is (Yes)
else (No)
stop
endif
}

@enduml