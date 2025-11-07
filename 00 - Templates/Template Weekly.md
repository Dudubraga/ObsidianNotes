###### [[{{date-1w:YYYY-[W]ww}}|<< Last week]] • [[Year-{{date: YYYY}}|{{date: YYYY}}]] • [[{{date+1w:YYYY-[W]ww}}|Next week >>]] 

# Week {{date:ww [from] Do MMMM}} to {{date+6d:Do MMMM GGGG}}

> [!todo]+ Tasks done this week
> ```dataview
> TASK
> WHERE completion > date({{date-1d:YYYY-MM-DD}}) AND completion < date({{date+7d:YYYY-MM-DD}})
> ```

> [!note]+ Mailbox
> ```dataview
> TABLE WITHOUT ID
> "[["+file.name+"|"+dateformat(file.day,"cccc")+"]]" as "day of week", inbox, outbox
> FROM "CALENDAR/DAILY"
> WHERE file.day >= date({{monday:YYYY-MM-DD}})
> AND file.day <= date({{sunday:YYYY-MM-DD}})
> AND (inbox OR outbox)
> SORT file.day ASC
> ```

> [!todo]+ Habits
> ```dataview
> TABLE WITHOUT ID
> "[["+file.name+"|"+dateformat(file.day,"cccc")+"]]" as "day of week",
> choice(sum(sleepdur)<420 OR coffee>1,"❌","✅") as 🏅,
> coffee*☕ as ☕,
> choice(sum(workoutdur), sum(workoutdur)+" min", "❌") as 🚲,
> choice(readings[0], "✅", "❌") as 📖,
> choice(healthymeal, "✅", "❌") as 🍲,
> "<progress value='"+sum(sleepdur)/60+"' max='8'></progress>" as "sleep (of 8hrs)"
> FROM "CALENDAR/DAILY" 
> WHERE file.day >= date({{monday:YYYY-MM-DD}})
> AND file.day <= date({{sunday:YYYY-MM-DD}})
> SORT file.name ASC
> ```

> [!summary]+ Highlights of the day
> ```dataview
> TABLE WITHOUT ID
> "[["+file.name+"|"+dateformat(file.day,"cccc")+"]]" as "day of week",
> summary as "Diary Shorts"
> FROM "CALENDAR/DAILY"
> WHERE file.day >= date({{monday:YYYY-MM-DD}}) AND file.day <= date({{sunday:YYYY-MM-DD}})
> SORT file.day ASC
> ```

## Reflection

*Thoughts & Feelings about this week...*

## Next week's planning

> [!alarm]- Upcoming events next two weeks
> ```dataview
> TASK
> WHERE due > date({{sunday:YYYY-MM-DD}}) AND due < date({{date+3w:YYYY-MM-DD}})
> ```

*Three top prio projects you will work on next week?*
- **1st**
- **2nd**
- **3rd**
