---
layout: post
title:  "Hints : Accepting iCal Appts In Outlook When You Are The Organiser"
date:   2011-08-19 10:50:18 +0000
categories: hints tech messaging
---

A case I have been working on has highlighted to me just how little information there is about this rather useful knowlegebase article – so i decided I would quickly knock something up to make sure I can remember next time this little solution is needed.

If you have a centrally run system which spits out iCal files left right and centre, this might be right up your street. The issue occurs when you attempt to accept an appointment that you are listed as the organiser of. Assuming your system doesn’t automatically add the appointment to your calendar, you will be faced by two confliciting messages.

“As the meeting organizer, you do not need to respond to this meeting”

and

“This meeting could not be found in your calendar”

Up until Outlook 2007, as the organiser you would be able to accept the meeting – which would add it to your calendar, but now this is not possible – as OL 2007 and up attempt to prevent duplicate items with this handy message. The only issue being this stops your centrally generated iCal ever making it into your Caledar, and in turn messes up your ability to track responses.

The solution to this is a handy registry entry contained in the article : http://support.microsoft.com/kb/940403

This entry means that when you open up an iCal file – in which you are listed as the organiser, Outlook automatically adds the event to your caledar if its not already there. Allowing you the full benefits of having the meeting within Outlook, without having to create the iCal in Outlook/Exchange.

Useful Integration Tip !