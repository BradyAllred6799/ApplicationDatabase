# Teams Chat: Brady Allred & Santiago Carpio

---

**Brady Allred** — 11/14/2025 7:26 AM

Good morning Santiago!

We met over a Zoom call the other day — I am with T&OD. Our department is exploring a way to create new instruction guides using Articulate Rise 360, which basically creates an HTML page. If possible, I would like to practice how that might work on a test site before we create a new process for the rest of the design team, and Gwynn said you may be able to help with setting up a page on the website not open to the public that I could experiment with. Would that be a possibility?

---

**Santiago Carpio** — 11/14/2025 9:05 AM

Good morning! It is definitely possible. I have created a draft page on the site with the title "TEST Articulate Rise 360." As long as you only save and preview the page as a draft, it won't be available to the public.

I am not familiar with Articulate Rise 360. Is the output an HTML file or is it a web page being hosted elsewhere?

---

**Brady Allred** — 11/14/2025 9:10 AM *(attachment: chart-fields-navigating-financial-transactions-raw-T76fFW3X.zip)*

It is an HTML output — normally it is in a SCORM package but these will just be regular HTML with JS and CSS. Here is a zip example.

---

**Brady Allred** — 11/14/2025 9:14 AM

And thank you! I will find it in WordPress.

---

**Brady Allred** — 11/14/2025 9:15 AM

Also, that is a full course — our guides will be much smaller.

---

**Santiago Carpio** — 11/14/2025 9:27 AM

Are you hoping to recreate the HTML inside of WordPress, or are you looking to somehow upload the files onto the site?

---

**Brady Allred** — 11/14/2025 9:29 AM

I was thinking we could host the files in our Z-drive (<https://training.hr.ufl.edu/>) like we do now with our PDFs and other files, then create a link to the index.html that they could click — so an identical user experience, it just leads to one of these interactions instead of a document. This would be for new guides we are creating in the future; we are still moving forward with converting all the current guides to .docx and replacing them.

---

**Santiago Carpio** — 11/14/2025 9:32 AM

I understand now. That sounds like it would work, but would need to test it to make sure. Please let me know if I can help with anything else!

---

**Brady Allred** — 11/14/2025 9:33 AM

Sounds good, I will — and thank you again!

---

**Brady Allred** — 11/18/2025 7:41 AM

Hey Santiago, sorry to bother you. I am wondering how difficult it is to redirect users from a link to a PDF hosted on the training.hr.ufl drive. Is it something I could learn to do with WordPress and SiteImprove? We have just had a few instances where documents have been updated but we aren't ready to roll out the new updates everywhere and make that into a process yet.

---

**Santiago Carpio** — 11/18/2025 8:07 AM

Good morning, it depends on the link you are trying to redirect from. Is it a link to the HR website or is it a link to the Word document?

---

**Brady Allred** — 11/18/2025 8:09 AM

It would be going from:

<https://training.hr.ufl.edu/instructionguides/time&labor/personal_leave_days.pdf>

to:

<https://view.officeapps.live.com/op/view.aspx?src=https%3A%2F%2Ftraining.hr.ufl.edu%2Finstruction_guides_ada2%2Fhuman_resources%2Ftime_and_labor%2Ffor_employees%2Fpersonal_leave_days.docx>

And that would be the same setup for other redirects as well — it will always be from a PDF at a similar path to an Office Apps Live .docx at a similar path.

---

**Santiago Carpio** — 11/18/2025 8:20 AM

In that case, the redirect would certainly be doable as long as you have access to the training.hr.ufl.edu website. Do you know where this website is being hosted, or if it is a WordPress site?

---

**Brady Allred** — 11/18/2025 8:25 AM

To be honest I am not sure if it is accessible via WordPress or not. It is mapped to our machines as the "Z Drive" so everyone in our office refers to it as that, but its actual name from what I can see is "prd (\\ad.ufl.edu\ufit\services\iis-hosting\sites\training.hr.ufl.edu)".

---

**Santiago Carpio** — 11/18/2025 8:29 AM

I am not very familiar with how IT would have set that up. Normally I would use an .htaccess file to write redirects but that might not work in that environment. I would recommend asking the IT team that set up that Z Drive if a redirect can be set up.

---

**Brady Allred** — 11/18/2025 8:30 AM

Sounds good. I will ask around and see if I can find who set this up initially. Thanks for your help!

---

**Santiago Carpio** — 11/18/2025 8:31 AM

Of course, please feel free to let me know if you have any other questions.

---

**Brady Allred** — 11/18/2025 8:42 AM

Haha, funnily enough, it was set up so long ago nobody seems to remember who set it up. But it does bring up the question: do you have any recommendations for a better system of hosting our files?

---

**Santiago Carpio** — 11/18/2025 1:42 PM

I don't know of a better system for just file hosting. My guess is that either the UFIT hosting or cloud team helped set it up. Unfortunately, the UFIT hosting website doesn't give any good contact information. I would suggest filling out a ticket to the help desk to see if they can pass your question to the right team. Here is their form: <https://ufl.teamdynamix.com/TDClient/33/IT-Portal/Requests/TicketRequests/NewForm?ID=g6~M3v5svuk_&a…>

---

**Brady Allred** — 11/18/2025 1:43 PM

Thanks! I will reach out to them.

---

**Santiago Carpio** — 2/26 9:54 AM

Good morning Brady, I am doing some initial testing for the toolkit search plugin. To make sure that this strategy is working properly, would you happen to know how many documents are being linked on the toolkit pages?

---

**Brady Allred** — 2/26 9:59 AM

Ah, I can't give you an exact number unfortunately — there have been some additions and some that have been done away with since we started this process, and we are also still updating some. I do know that right now we have updated 763 files in our Z-drive but I couldn't tell you how many total links there are on the toolkits. I could do some investigating and let you know.

---

**Santiago Carpio** — 2/26 10:01 AM

No worries, even a range would be helpful. I was getting over 1,300+ Word docs originally and after some changes I am getting 634 Word docs. I was wondering which was in the right ballpark.

---

**Brady Allred** — 2/26 10:02 AM

Yeah, that is quite the range. I will do some checking and get back with you. Thank you for your help with this.

---

**Santiago Carpio** — 2/26 10:08 AM

Thanks!

---

**Brady Allred** — 2/26 10:30 AM

This is the report my crawler gave:

```
=== INDEX BUILD STATS REPORT ===

HTML pages fetched (parsed): 91
Total <a href> links seen: 42,420

Doc link instances seen (includes duplicates across pages): 734
Unique document files seen: 644

Unique docs by file type:
  .docx: 633
  .pptx: 3
  .xlsx: 8

Doc link instances by file type:
  .docx: 722
  .pptx: 4
  .xlsx: 8

Index rows written (doc-location pairs): 723
Unique docs downloaded/parsed (doc_cache size): 644
Download/parse failures: 0

Pages scanned:

Step 1: Crawling Website for Navigation Structure + Document Links...
  Scanning: Toolkits
  Scanning: Career Toolkits > Career Development Hub
  Scanning: Leadership Development Toolkit
  Scanning: New Manager Toolkit
  Scanning: UF Engaged Toolkit
  Scanning: Financial Toolkits
  Scanning: Financial Toolkits > Asset Management
  Scanning: Financial Toolkits > Budget Checking
  Scanning: Financial Toolkits > Budget & Commitment Control
  Scanning: Financial Toolkits > Chartfields
  Scanning: Financial Toolkits > Deposits
  Scanning: Financial Toolkits > Distance Learning
  Scanning: Financial Toolkits > Grants
  Scanning: Financial Toolkits > Journal Entry
  Scanning: Financial Toolkits > Managerial Budgets
  Scanning: Financial Toolkits > myUF Marketplace
  Scanning: Financial Toolkits > Paying Vendors (for DSOs)
  Scanning: Financial Toolkits > Procurement
  Scanning: Financial Toolkits > Reconciliation
  Scanning: Financial Toolkits > Research Participant Payments
  Scanning: Financial Toolkits > Travel and Expense
  Scanning: Financial Toolkits > UF Budget Planner
  Scanning: Mainspring
  Scanning: Mainspring > Recommended Training Pathways
  Scanning: Mainspring > Human Resources Competencies
  Scanning: Mainspring > Financial Competencies
  Scanning: Mainspring > Compliance Competencies
  Scanning: Mainspring > Professional Competencies
  Scanning: Mainspring > Grantsmanship Competencies
  Scanning: Mainspring > Together We Drive UF Research
  Scanning: Human Resources Toolkits
  Scanning: Human Resources Toolkits > Careers at UF
  Scanning: Human Resources Toolkits > Commitment Accounting
  Scanning: Human Resources Toolkits > Effort Reporting
  Scanning: Human Resources Toolkits > Faculty Searches
  Scanning: Human Resources Toolkits > Hiring and Additional Pay
  Scanning: Human Resources Toolkits > Job and Position Actions
  Scanning: Human Resources Toolkits > myTraining
  Scanning: Human Resources Toolkits > myTraining Partner Program
  Scanning: Human Resources Toolkits > ONE.UF Time Approval
  Scanning: Human Resources Toolkits > Person of Interest
  Scanning: Human Resources Toolkits > Time and Labor
  Scanning: Enterprise Analytics
  Scanning: Student Information Systems
  Scanning: Student Information Systems > Academic Advising
  Scanning: Student Information Systems > College and Department Scholarships
  Scanning: Student Information Systems > Course Catalog (Campus Solutions)
  Scanning: Student Information Systems > Course Fees
  Scanning: Student Information Systems > Course & Room Scheduling
  Scanning: Student Information Systems > Course Transfer Evaluation (Undergraduate)
  Scanning: Student Information Systems > Degree Certification
  Scanning: Student Information Systems > Grades
  Scanning: Student Information Systems > Graduate School
  Scanning: Student Information Systems > MyAdmissions
  Scanning: Student Information Systems > Non-Degree Approval
  Scanning: Student Information Systems > ONE.UF
  Scanning: Student Information Systems > Registration
  Scanning: Student Information Systems > Service Indicators
  Scanning: Student Information Systems > SIDA (Student Initiated Drop/Add)
  Scanning: Student Information Systems > Student Financials
  Scanning: Student Information Systems > Student Groups
  Scanning: Student Information Systems > Student Program/Plan
  Scanning: Student Information Systems > Student Services Center
  Scanning: Student Information Systems > Undergraduate Catalog Publication
  Scanning: Student Information Systems > Undergraduate Minors
  Scanning: Sponsored Programs
  Scanning: General Toolkits
  Scanning: General Toolkits > UFDocuSign
  Scanning: General Toolkits > Security Roles
  Scanning: General Toolkits > Identity Management
  Scanning: General Toolkits > myUFL Basics
  Scanning: Teamwork and Collaboration Toolkit
  Scanning: Teamwork and Collaboration Toolkit > Accountability
  Scanning: Teamwork and Collaboration Toolkit > Shared Purpose/Goals
  Scanning: Teamwork and Collaboration Toolkit > Trust
  Scanning: Teamwork and Collaboration Toolkit > Communication
  Scanning: Teamwork and Collaboration Toolkit > Clear Structure and Alignment
  Scanning: Teamwork and Collaboration Toolkit > Resources
  Scanning: Hiring at UF Toolkit
  Scanning: Career Toolkits
  Scanning: Career Toolkits > Career Catalyst: Building your Professional Journey at UF
  Scanning: Career Toolkits > Career Collab
  Scanning: UF GO Toolkit
  Scanning: UF GO Toolkit > Profile
  Scanning: UF GO Toolkit > Request
  Scanning: UF GO Toolkit > Travel
  Scanning: UF GO Toolkit > Expense
  Scanning: UF GO Toolkit > Approvals
  Scanning: UF GO Toolkit > Mobile
  Scanning: Faculty Excellence and Advancement
  Scanning: Student Information Systems > Simple Syllabus

Step 2: Writing outputs...

SUCCESS! Index built with 723 entries.
Doc cache size: 644 unique documents.
```

---

**Santiago Carpio** — 2/26 10:32 AM

Awesome! I think we should be in the right ballpark now. Thanks!

🙏 1

---

**Brady Allred** — 2/27 11:17 AM

Hey Santiago, I am not sure who requested this but Gwynn asked me to update the links to instruction guides on this page, but it doesn't look like I have permissions to edit here. Would you be able to help me either get the requisite permission or connect with whoever has that permission so I can provide them the updated links?

*(myUFL | Current Employees — hr.ufl.edu)*

---

**Santiago Carpio** — 2/27 11:24 AM

I have updated the permissions, you should be able to access it now. Please let me know if you still can't.

---

**Brady Allred** — 2/27 11:26 AM

Got it, thank you!

---

**Brady Allred** — 4/6 2:12 PM

Hey Santiago, you can ignore that email — I apologize, I added you by mistake.

---

**Santiago Carpio** — 4/6 2:19 PM

Hey Brady, no worries! Thanks for letting me know.

---

**Brady Allred** — 4/8 1:21 PM

Good afternoon Santiago!

When you have a moment I just have a quick question that you may or may not have an answer to. We have noticed that the Office Live view for some of our instruction guides sometimes takes a while to load. Do you have any clue what may cause that?

Here is one for example that took a while for me just now:
<https://view.officeapps.live.com/op/view.aspx?src=https%3A%2F%2Ftraining.hr.ufl.edu%2Finstruction_g…>

---

**Santiago Carpio** — 4/8 1:42 PM

Good afternoon Brady! Unfortunately I don't know why. It's possible it could be on the training.hr.ufl.edu / Z-drive end, so maybe UFIT might know or have configurations they can take a look at.

---

**Brady Allred** — 4/8 1:43 PM

Sounds good, thank you!

---

**Brady Allred** — 4/13 11:04 AM

Hey Santiago, I am not sure who requested this but Gwynn said someone asked you for the updated "Creating a Check Request" instruction guide. That one was apparently not on our toolkit so I am not sure where they were finding it, but consequentially it had not been updated yet. I just finished that conversion, and here is the updated link:

Creating_a_Check Request.docx

---

**Santiago Carpio** — 4/13 11:06 AM

Hi Brady, thanks for doing that. The request came from the CFO so they must have been linking to an old guide. I'll pass this along to them.

💯 1

---

**Santiago Carpio** — 5/6 8:12 AM

Good morning Brady, how are you doing? Have you been able to recover well?

---

**Brady Allred** — 5/6 8:15 AM

Morning! Yes, recovering well and back in the office now!

---

**Santiago Carpio** — 5/6 8:22 AM

That's great to hear!

I had some questions about the Training team's Z-drive. I understand UFIT set it up but was wondering if that type of drive had a name. Communications is considering options for managing files for the website and we wanted to know more about how the Z-drive worked given it has its own domain and you can link to files on it.

---

**Santiago Carpio** — 5/6 8:24 AM

If there's any info you know about the Z-drive, I'd greatly appreciate it. If you'd prefer, we can hop on a quick call as well.

---

**Brady Allred** — 5/6 9:55 AM

Ah, that makes sense. To be honest, I don't know a ton about it — I am not sure where it is physically located. The drive is actually named "prd (\\ad.ufl.edu\ufit\services\iis-hosting\sites\training.hr.ufl.edu)."

Looking at the properties and permissions, it has the owner listed as "ict-mps-svc-create (<ict-mps-svc-create@ad.ufl.edu>)" and an admin listed as <conleydamron@ufl.edu>, along with a few other UFIT generic accounts.

---

**Santiago Carpio** — 5/6 10:44 AM

This is helpful! The "iis-hosting" actually clues me in to what service this is. I'll reach out to UFIT for more info. Thanks!

---

**Brady Allred** — 5/6 10:50 AM

Anytime! Glad it was helpful!

---

**Brady Allred** — 5/12 4:29 PM

Hey Santiago, I wanted to touch base on the search index app — I know we had something on the calendar for when I was out.

---

**Santiago Carpio** — 5/12 4:32 PM

Hey Brady, yes we had canceled our meeting until you were back. I can find a good time to schedule a meeting soon to take a look at that again.

---

**Brady Allred** — 5/13 8:02 AM

Perfect, thank you! Let me know when works.

---

**Santiago Carpio** — 5/13 8:19 AM

I just sent a meeting invite for Monday at 10am. Let me know if that doesn't work for you.

---

**Brady Allred** — 5/13 8:28 AM

That works! See you then.
