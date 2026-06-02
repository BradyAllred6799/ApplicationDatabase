# Email Chains: UFHR Toolkit Search Tool & Document Update Process

*Participants: Brady Allred, Gwynn Cadwallader, Patricia Alba, Santiago Carpio, Mitchell Galloway, and others*

---

## Chain 1: T&OD Website Documents Update Process

---

**Brady Allred** — Friday, January 16, 2026 12:22 PM
**To:** Santiago Carpio, Patricia Alba | **Cc:** Gwynn Cadwallader

Hi Santiago and Patricia,

I am getting ready to update the document links on the HR Training website to the new ADA-compliant documents. To make the process faster and error-proof, I wrote a Python script with AI to help manage the workflow. I wanted to run it by you first.

What it does: It scans our Z: drive to generate the new Office Web Viewer links and automatically "pings" them to ensure they aren't broken. It then creates a local dashboard that helps me quickly swap the old links for the new, valid ones inside WordPress.

We were wondering if it would be best to create temporary drafts of each page we updated to make sure the changes take effect and don't break anything, or if just using the preview feature to check would be good enough.

Thank you and I would love to hear your thoughts.

---

**Gwynn Cadwallader** — Friday, January 16, 2026 1:52 PM
**To:** Brady Allred, Santiago Carpio, Patricia Alba

This is some pretty cool work, Brady!!

Patricia — we will want to queue up the UF @ Work story about the new format of the IGs once Brady is ready.

Thanks!

---

**Patricia Alba** — Friday, January 23, 2026 3:28 PM
**To:** Gwynn Cadwallader, Brady Allred, Santiago Carpio

Hi Gwynn,

Please remind me, is this just for the IGs in the toolkit page? <https://hr.ufl.edu/professional-development/toolkits/human-resources-toolkits/>

We'll want a UF at Work article letting people know we've updated the toolkit to be ADA compliant, and that they should update any bookmarks they've saved.

Let me know if I missed something. Thank you.

---

**Gwynn Cadwallader** — Monday, January 26, 2026 9:47 AM
**To:** Patricia Alba, Brady Allred, Santiago Carpio

Good morning Patricia,

For now it is just IGs in the toolkit page: <https://hr.ufl.edu/professional-development/toolkits/human-resources-toolkits/>

Brady will be starting to make the new version live on Wednesday 1/28 and the updating process will continue over the next few weeks.

Thanks!

---

**Patricia Alba** — Wednesday, February 4, 2026 4:51 PM
**To:** Gwynn Cadwallader, Brady Allred | **Cc:** Jordyn Thoreson, Santiago Carpio

Hi Gwynn and Brady,

I have the below queued up for UF at Work:

> **UFHR toolkits updated to meet accessibility guidelines**
> The UFHR Training and Organizational Development team has updated its training toolkits to meet accessibility guidelines as set forth by ADA Title II regulations. As part of this update, all instructions guides were updated to read-only Word documents. Faculty and staff are encouraged to review and update their bookmarks for the latest toolkit. If you have any questions, contact the training team at <training@ufl.edu>.
>
> Explore: <https://hr.ufl.edu/professional-development/toolkits/>

Gwynn, in today's HR Forum you mentioned updates will continue through February. Would you like us to wait until everything is done to send this out in UF at Work? Otherwise, we can queue it up for next week.

Thank you.

---

**Gwynn Cadwallader** — Thursday, February 5, 2026 6:23 AM
**To:** Patricia Alba, Brady Allred | **Cc:** Jordyn Thoreson, Santiago Carpio

Good morning!

I think we are ready for the UF at Work article. We have the bulk of the guides uploaded and reviewed. Only the SIS guides remain in the old format.

Brady — any reservations? Thank you!

---

**Brady Allred** — Thursday, February 5, 2026 12:38 PM
**To:** Gwynn Cadwallader, Patricia Alba

None from me, thank you all for your help!

---

## Chain 2: Links within Word Docs on the Websites

---

**Brady Allred** — Wednesday, January 28, 2026 7:58 AM
**To:** Patricia Alba, Santiago Carpio | **Cc:** Gwynn Cadwallader

Good morning all,

In the process of updating our instruction guides, we realized one problem we will have is the links to instruction guides that are inside other instruction guides. Right now, the hyperlinks in the new guides reference old instruction guides that are all about to be replaced. We were wondering if SiteImprove might be able to help us with this. Do you know if it is capable of finding broken links within documents linked on the broken pages? IE, will it detect if a Word .docx file has broken links in it?

Would love your thoughts on addressing this issue, thank you!

---

**Santiago Carpio** — Wednesday, January 28, 2026 8:55 AM
**To:** Brady Allred, Patricia Alba | **Cc:** Gwynn Cadwallader

Good morning,

SiteImprove only seems to detect broken links inside PDF documents, so it sounds like that won't work for the Word documents. If your team is able to track and record the old PDF links and the new Word links that are replacing them, I could set up redirects as a short-term solution.

Please let me know what you think. Thanks!

---

**Brady Allred** — Thursday, February 12, 2026 4:13 PM
**To:** Santiago Carpio, Patricia Alba | **Cc:** Gwynn Cadwallader

Thank you Santiago, I apologize — I completely forgot to respond. I ended up just building a script that scanned all of our documents looking for links to PDF files within them and just updating them there. A little tedious, but it worked.

On another matter though, we held a meeting with a focus group to talk about how we can improve our instruction guides and the biggest piece of feedback we got was that they are hard to find. In response to this, I built an index hosted on our Z-drive that allows them to search just our instruction guides to help them find what they need. We are wondering if you have any suggestions on how to implement it, as it is not a WordPress site. The options I am thinking are either embed it in an iframe or simply create a link to it on our toolkit page, but wanted to see if you had any thoughts.

Additionally, right now the only way to update the index is running a script on my local machine. It scans our Z-drive and the toolkit web pages to create a JSON file that the index.html uses to find the data. I experimented with trying to automate this process but I don't have access to the actual server to set up a way for the script to run every so often. Do you have any suggestions?

I have attached the link to the live web page, as well as copies of the search tool production files that show how the index process works, and some screenshots of my view of the Z drive that may help explain the set up.

- **Live Web page:** [UF Instruction Guide Library](https://training.hr.ufl.edu/search_tool/index.html)
- **Toolkit Parent Page:** [Toolkits | Current Employees](https://hr.ufl.edu/professional-development/toolkits/)

---

**Santiago Carpio** — Friday, February 13, 2026 10:24 AM
**To:** Brady Allred, Patricia Alba | **Cc:** Gwynn Cadwallader

Good morning Brady,

Nice work in speeding up the update process and coming up with this tool for searching!

Before implementing it, I need to ask that you make sure that the code is properly sanitizing and validating searches and input from users. That can be a security risk and open the door to a XSS vulnerability. If you need any help with that, please let me know.

In terms of adding the tool to the site, an iframe or a link would be the simplest solutions. If a more integrated solution is desired, we would probably need to discuss development of a custom WordPress plugin that can insert the search tool on a page. This would become a project that will require time to develop.

For automating the index update, I have access to the web server, and we can host the Python script and create a cron job that will execute the script periodically at a certain schedule. I am not sure if that would still be able to interact with your Z-drive, so that might be a question for IT.

Please let me know if you have any questions or how you would like to move forward!

---

**Brady Allred** — Friday, February 13, 2026 1:41 PM
**To:** Santiago Carpio, Patricia Alba | **Cc:** Gwynn Cadwallader

Thanks for getting back so quickly and looking at this, Santiago!

Using ChatGPT, I believe that the code in this latest version is secure and sanitizing and validating correctly, but if you are able to glance it over to verify, I would really appreciate it. If not, no worries — just let me know and I will look for other options. I definitely do not want to cause a security risk, but my expertise is quite limited.

I think an iframe or link is probably the best option; we don't want to spend too much time on this, as we are unsure of what changes to our system may come with Workday anyway.

For the automatic update, it might just be simplest if I reach out to IT first, as access to the Z drive is needed for the scan, but I do appreciate all of your help with this.

---

**Santiago Carpio** — Monday, February 16, 2026 9:28 AM
**To:** Brady Allred, Patricia Alba | **Cc:** Gwynn Cadwallader

Good morning Brady,

Thank you for updating the code. As I understand, the tool is looking at both the toolkit webpages and the Z-drive. To clarify, what is the purpose of it interacting with the Z-drive when the documents are linked on the webpages?

Additionally, to make sure we are following security standards and not introducing any potential vulnerabilities to our systems or data, I would like to suggest a few ways forward.

The first would be to submit a risk assessment request of the search tool to the Information Security team at IT. You can find more information on how to do that at IT's [Risk Requests and Assessments](https://it.ufl.edu/security/audiences/faculty--staff/irm/risk-requests-and-assessments/) page. IT would review the tool and if they approve, we can move forward with adding it to the website with a link or iframe.

The other option would be for my team to develop a WordPress plugin that has the same functionality of searching only the toolkit documents. Since it would use WordPress's built-in functions and integrate as an internal tool within the website, we could be confident of its security. My estimate would be that developing a search plugin like this could take up to two months on our end.

Please let me know what you think. It is best that we cover all our bases so neither our WordPress sites nor your team's Z-drive are put at risk, but I'm looking forward to how we can improve our toolkits!

---

**Gwynn Cadwallader** — Monday, February 16, 2026 10:07 AM
**To:** Santiago Carpio, Brady Allred, Patricia Alba

Hi all,

We think the index and its searchability are very important in assisting people to locate the resource they need within the toolkits. If this can be done with a WordPress plug-in, that is probably the best. Our preference is that it updates automatically when the content is changed or updated.

This has been a key pain point for employees when using the Toolkits. Let us know how we can help.

Thanks for your partnership!

---

**Brady Allred** — Monday, February 16, 2026 3:19 PM
**To:** Gwynn Cadwallader, Santiago Carpio, Patricia Alba

Hello Santiago and all,

Thanks for getting back with me! The purpose of the script scanning the Z drive was to ensure the documents were searchable. I did not realize that the crawler could get that data from the links on the website itself. I have since modified the script so it doesn't scan anything on the Z-drive, just the toolkit web pages.

I have also submitted a request to have the tool reviewed. Thank you for getting me to the right place. I am not sure what their process is at this point, but I imagine I will hear from them soon, and we can move forward from there.

Thanks again for all your help.

---

**Patricia Alba** — Monday, February 16, 2026 3:33 PM
**To:** Brady Allred, Gwynn Cadwallader, Santiago Carpio

Hi Brady,

Gwynn mentioned moving forward with Santiago's suggestion of a WordPress plugin rather than the script. I feel more secure if we also move forward this way, rather than use something that needs to go through risk assessment. The plugin will also be seamlessly integrated into our website and we'll know there are no security risks.

We can schedule a meeting to discuss customization of the plugin and what would work best for your team. Let me know if this works for you all and I can put something in our calendars.

Thank you.

---

**Brady Allred** — Monday, February 16, 2026 3:35 PM
**To:** Patricia Alba, Gwynn Cadwallader, Santiago Carpio

Apologies, I read Gwynn's email in a rush — been a busy day. Yes, let's move forward with that option. Thank you!

---

**Gwynn Cadwallader** — Tuesday, February 17, 2026 6:35 AM
**To:** Patricia Alba, Brady Allred, Santiago Carpio

Thank you all! This will be a huge win for campus. 😊 We are happy to contribute where it makes sense. I am so excited about this.

---

**Santiago Carpio** — Friday, April 10, 2026 3:25 PM
**To:** Gwynn Cadwallader, Patricia Alba, Brady Allred

Hello all,

I am happy to report that we have completed a working version of the HR Toolkit document search tool in WordPress. It is currently active in our test website where you can go and test the tool: <https://test.hr.ufl.edu/professional-development/toolkit-document-search/>. The plugin outputs a search bar where visitors can input a query, and the plugin will return cards that link to matching documents and the toolkit pages they are found on. On the backend, this plugin is scanning the site every night and updating the library of links to any Word, PowerPoint, and Excel files that exist in the toolkits along with the pages they are found on.

I will look to find a time next week when we can all meet to demo the tool and discuss any feedback you may have.

Please keep an eye out for a meeting invitation and let me know if you have any questions.

---

**Brady Allred** — Monday, April 13, 2026 7:39 AM
**To:** Santiago Carpio, Gwynn Cadwallader, Patricia Alba

This is great!

Thank you so much for your work on this, Santiago!

---

**Santiago Carpio** — Monday, May 18, 2026 10:21 AM
**To:** Brady Allred, Gwynn Cadwallader, Patricia Alba, Mitchell Galloway

Hi everyone!

Here is the link again to the Toolkit Document Search test page:

<https://test.hr.ufl.edu/professional-development/toolkit-document-search/>

Please let me know if any questions come up!

---

**Gwynn Cadwallader** — Monday, May 18, 2026 2:45 PM
**To:** Santiago Carpio, Brady Allred, Patricia Alba, Mitchell Galloway

Thank you!

---

## Chain 3: Toolkit Document Search Feedback

---

**Brady Allred** — Wednesday, May 20, 2026 8:14 AM
**To:** Santiago Carpio, Patricia Alba | **Cc:** Gwynn Cadwallader
**Subject:** Toolkit Document Search Feedback

Morning Santiago and Patricia!

We have had overwhelmingly positive feedback on the toolkit document search — definitely something that people are going to be excited about. Thank you so much for all of your hard work on this; it really is going to have a positive impact and make resources easier to find.

One thing that was requested was the ability to include UF policies in the search as well. I'm not sure how that would work, or if that could be done, but we wanted to run it by you and see if that was something that could be added? Acknowledging that it may be a 2nd iteration of the product, as it goes beyond the original scope of the project and I know you are really busy. Let me know your thoughts.

The only problem we saw was a typo issue where it seems like for some reason the "doc" in words like "documents" is being cut off.

*(screenshot attached)*

Thank you again — this is a huge improvement to the site.

---

**Santiago Carpio** — Wednesday, May 20, 2026 10:26 AM
**To:** Brady Allred, Patricia Alba | **Cc:** Gwynn Cadwallader

Good morning!

I am happy to hear that the toolkit has received such positive feedback, and others are finding it helpful!

About the UF policies, I have some questions and would need to think through how that might work with this tool. Are these policies that are being included or linked to from the toolkits? Or is the desire to have all UF policies included in the tool? UFIT already has a searchable [policy hub](https://policy.ufl.edu/) so I would be curious if this is not already meeting that need. If needed, we can discuss this whenever we have our next meeting.

Thank you for pointing out that bug about "doc" being cut out of titles. I've just updated the plugin and it seems to be capturing the text correctly now.

---

**Gwynn Cadwallader** — Thursday, May 21, 2026 8:10 AM
**To:** Santiago Carpio, Brady Allred, Patricia Alba

Hi Santiago,

Below is the feedback so you can see what they were thinking. I know on the FIN side that many policies are changing. Just wanted to share because this also seems like a pain point but not really related to the toolkits. I didn't make any promises — just sharing what seems like a good idea.

Gwynn

---

*From Matt:*

This is an amazing idea! I was able to find a few things but I wonder if what I am searching for in some instances is out of scope.

I wasn't able to get a hit on most of the keywords for guides on this page: <https://cfo.ufl.edu/procedures-training-resources/> — things like construction projects, or the ever-so-popular Business/Entertainment Policy.

Or this page: <https://research.ufl.edu/uf-policies-and-guidelines> which has guidelines on things like cost share or research agreement templates.

Maybe I am looking for policies whereas the tool is geared more towards training/IGs? There is some overlap there, but not always.

---

*From Carrie:*

I searched for a few things and it is great! It took me exactly where I needed to go. I did notice that it is best to use high level terms as people call things differently across the university, so guidance on searching would be good, but I think most people can figure it out.

I know this is only toolkits, but can a link be included to the policies on a given subject (in the landing page of the topic — not searchable necessarily)?

---

**Santiago Carpio** — Thursday, May 21, 2026 3:32 PM
**To:** Gwynn Cadwallader, Brady Allred, Patricia Alba

Hi Gwynn,

Thank you for sharing that feedback. It seems like there is some lack of clarity that this tool is only searching from the toolkits under the HR website. That might be something we can clarify with some text above the search bar. I could see having a link to the UF Policy Hub as a potential way to point people in that direction if that is what they are looking for. Building the system to include all the documents in other websites might be difficult to integrate and maintain.

Regarding some of the ideas from our meeting, I've implemented a way to include a floating button on the right-side column where the page contents menu appears. You can see an example on this test page: <https://test.hr.ufl.edu/professional-development/toolkits/new-manager-toolkit>. Additionally, if the page doesn't have a page contents menu, a link to the search tool can be highlighted near the top of a page such as on this test Toolkits page: <https://test.hr.ufl.edu/professional-development/toolkits/>.

Please take a look whenever you have the chance and let me know if you have any feedback.

---

**Gwynn Cadwallader** — Tuesday, May 26, 2026 12:34 PM
**To:** Santiago Carpio, Brady Allred, Patricia Alba

It works great for me! I think we can proceed with the communication plan and deploy. 😊

Great work!!

---

## Chain 4: Request for Testing — New UFHR Toolkit Search Tool

---

**Gwynn Cadwallader** — Monday, May 18, 2026 10:46 AM
**To:** Carrie Pridgeon, Terry Moore, Barb Mitola, Matthew Walters, Nikki Kelton, Becky Redmond, Yerimye Bloomfield, Jaymes Gillett, Audrey Gainey | **Cc:** Brady Allred, Mitchell Galloway, Sarah Hanson, Fidela James, David Smith
**Subject:** Request for Testing: New UFHR Toolkit Search Tool

Good morning,

We have some exciting news to share! We've developed a new search tool for the UFHR Toolkits and would like your help testing it.

As you know, end users often have difficulty locating the instructional guides (IGs) they need because the toolkits contain more than 15,000 documents. This new search tool is designed to make it much easier to find relevant resources.

Please use the test link below to explore the tool and see whether the search results match what you would expect based on different keywords:

<https://test.hr.ufl.edu/professional-development/toolkit-document-search/>

We ask that you spend no more than 30 minutes testing the site.

The search results will display:

- Documents containing your search term
- The category and sub-toolkit where each document is located

To get started, try searching for "budget" to see how the results are organized.

Please send your feedback to me by May 26 via email. We will use your input to make any final adjustments before launching the tool and promoting it to GBAS, HRL, and through UF at Work.

Thank you in advance for your time and assistance!

---

**Becky Redmond** — Wednesday, May 27, 2026 12:37 PM
**To:** Gwynn Cadwallader

Hi Gwynn,

What a wonderful tool!

My feedback:

Some keywords might not be intuitive — I tried "I9" and got no results, while "I-9" returned results.

Neither "W4" nor "W-4" returned results. "Tax" and "taxes" did not return results. How to make W-4 edits should be searchable, I think.

Is there a way to make the tool more sensitive to different ways of referring to a topic? Especially when forms are referred to regularly rather than the process (like I9s).

I looked up "PDL" and "Professional Development Leave," with no results returned for either search.

No search results for "name change."

I did get some great search results for some of my keywords!

Also, I missed the deadline, and I apologize. We are in the midst of a huge reorganization in IFAS Extension — Extension Districts are going away eff 7/1/26, which affects supervision and a whole host of other HR changes that we are scrambling to identify and process. 😊

Thank you, Becky Redmond

---

**Gwynn Cadwallader** — Wednesday, May 27, 2026 12:42 PM
**To:** Brady Allred, Santiago Carpio, Mitchell Galloway | **Cc:** Patricia Alba
**Subject:** FW: Request for Testing: New UFHR Toolkit Search Tool

Some feedback for the search tool.

*(Forwarding Becky Redmond's email above.)*

---

**Santiago Carpio** — Wednesday, May 27, 2026 2:12 PM
**To:** Gwynn Cadwallader, Brady Allred, Mitchell Galloway | **Cc:** Patricia Alba

Hello Gwynn,

Thank you for passing along that feedback to us and the go-ahead to proceed! I will add the search tool to its own page on the live site and add buttons to the toolkit pages linking to the search tool like we discussed.

I will look into improving the search to handle situations like with the I-9 documents. However, the scope of the search tool is limited to the documents in the toolkits section of the HR site, so any documents or topics outside of that will not appear in the search.

As a heads up, I will be out of the office for a month starting this Friday, May 29th, so it may take some time before I can implement any major changes to the search.

Please let me know if there are any other feedback or questions.

---

**Gwynn Cadwallader** — Wednesday, May 27, 2026 2:16 PM
**To:** Santiago Carpio, Brady Allred, Mitchell Galloway, Patricia Alba

Thanks Santiago.

I will defer to you all on any additional features/functionality. The group has good ideas but we may not have the bandwidth to act on all of them.

@Patricia Alba — I'd love to share at the HR Forum in June if that is not too soon for the communication.

Appreciate all the great work!

---

**Patricia Alba** — Wednesday, May 27, 2026 7:41 PM
**To:** Gwynn Cadwallader, Santiago Carpio, Brady Allred, Mitchell Galloway

Hi Gwynn,

This sounds good to me. We have the UF at Work article queued up for June 15. We'll mention that the toolkits were updated for ADA, for people to refresh their bookmarks, and add a plug about the search feature.

We met with Becky and David yesterday regarding the reduction in training courses next year. We're prioritizing and scheduling that announcement for June 8. We'll do a follow up in the fall as well. I recommend also mentioning this in the HR forum.

Best, Patricia
