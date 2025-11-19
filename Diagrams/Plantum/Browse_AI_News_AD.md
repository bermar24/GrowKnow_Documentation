@startuml
title Browse AI News Activity Diagram

|User|
start
:Opens "AI News" section;

|System|
:Displays initial feed of recent AI news items;

split
|User|
:Uses search box or applies filters;
|System|
:Checks for results based on new criteria;

    if (Are there results?) then (No)
        :Displays "no articles" message and suggestions;
    else (Yes)
        :Displays the narrowed list of AI news items;
    endif

split again

    |User|
    :Clicks a news item;
    |System|
    :Attempts to load the details view;
    
    if (Network/API connection OK?) then (No)
        :Shows error message with a retry option;
        
        |User|
        if (Retry?) then (Yes, Retry)
            |System|
            ->Attempts to load the details view;
        else (No, Exit)
            end
        endif
    else (Yes)
        :Displays details view (full article text and related links);
        |User|
        :Reads the article and/or uses related links;
        end
    endif
end split

stop
@enduml