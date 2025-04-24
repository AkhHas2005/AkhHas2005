# Using Relative URLs in SharePoint  

## Me
How I can I use the relative url of a webpage stored in the team documents section of sharepoint in a page stored in the pages section of sharepoint?  

## Co-Pilot
[1]: https://support.microsoft.com/en-us/office/create-and-use-modern-pages-on-a-sharepoint-site-b3d46deb-27a6-4b1e-87b8-df851e503dec ""
[2]: https://support.microsoft.com/en-us/office/using-web-parts-on-sharepoint-pages-336e8e92-3e2d-4298-ae01-d404bbe751e0 ""
[3]: https://www.youtube.com/watch?v=eK3XoK8kbio ""
[4]: https://learn.microsoft.com/en-us/sharepoint/dev/general-development/urls-and-tokens-in-sharepoint ""
[5]: https://smallbusiness.chron.com/use-relative-links-sharepoint-51410.html ""
[6]: https://stackoverflow.com/questions/1634449/relative-urls-in-sharepoint-master-page ""
[7]: https://sharepoint.stackexchange.com/questions/105619/how-to-add-a-relative-url-link-to-a-page-from-a-link-button-on-a-web-part-sharep ""

Certainly! When working with SharePoint, you can use relative URLs to link between different pages or resources. Here's how you can use relative URLs in your scenario:

1. **Domain-Relative URL**:
   - A domain-relative URL begins with a forward slash (`/`) and specifies a complete path from the top-level website to the file name.
   - For example: `/sites/Web_Site/Lists/List_Title/AllItems.aspx`.

2. **Website-Relative URL**:
   - A website-relative URL is based on the address of a website object (SPWeb). It does not begin with a forward slash.
   - For example: `Lists/List_Title/AllItems.aspx`.

3. **URL Tokens**:
   - SharePoint supports tokens that you can use in URLs for various situations in development.
   - These tokens can be used in custom actions, links on custom pages, and more.
   - Some tokens are usable only in apps, so be aware of context-specific restrictions.
   - For more details, refer to the [URLs and tokens in SharePoint documentation](https://learn.microsoft.com/en-us/sharepoint/dev/general-development/urls-and-tokens-in-sharepoint).

Remember to adjust the URLs based on your specific SharePoint setup. If you need further assistance, feel free to ask! 😊

Learn more: [1. support.microsoft.com](https://support.microsoft.com/en-us/office/create-and-use-modern-pages-on-a-sharepoint-site-b3d46deb-27a6-4b1e-87b8-df851e503dec) 
[2. support.microsoft.com](https://support.microsoft.com/en-us/office/using-web-parts-on-sharepoint-pages-336e8e92-3e2d-4298-ae01-d404bbe751e0) 
[3. www.youtube.com](https://www.youtube.com/watch?v=eK3XoK8kbio) 
[4. learn.microsoft.com](https://learn.microsoft.com/en-us/sharepoint/dev/general-development/urls-and-tokens-in-sharepoint) 
[5. smallbusiness.chron.com](https://smallbusiness.chron.com/use-relative-links-sharepoint-51410.html) 
[6. stackoverflow.com](https://stackoverflow.com/questions/1634449/relative-urls-in-sharepoint-master-page) 
[7. sharepoint.stackexchange.com](https://sharepoint.stackexchange.com/questions/105619/how-to-add-a-relative-url-link-to-a-page-from-a-link-button-on-a-web-part-sharep)  

## Me
If my page is called EHM-Guides-(AI-Searchable).aspx and is stored in the site Children's System Support and my webpage I want to link is called index.html in the folder AI-Search in Documents, how can I link to it as a awebpage and not as a file?  

## Co-Pilot
To link to the webpage "index.html" stored in the "AI-Search" folder within the "Documents" section of your SharePoint site, you can create a hyperlink using the domain-relative URL. Here's how:

1. First, determine the domain-relative URL for your target page:
   - If your SharePoint site is named "Children's System Support," the domain-relative URL would be: `/sites/ChildrensSystemSupport/Documents/AI-Search/index.html`.

2. Next, create a hyperlink on your "EHM-Guides-(AI-Searchable).aspx" page:
   - Use an anchor tag (`<a>`) with the `href` attribute set to the domain-relative URL.
   - Example: `<a href="/sites/ChildrensSystemSupport/Documents/AI-Search/index.html">Link to AI-Search</a>`

This will create a clickable link to your webpage. Adjust the URL based on your specific SharePoint setup. Let me know if you need further assistance! 😊  

## Me
How can I upload a webpage to the web for free so that I can access it from a link?  

## Co-Pilot
[2]: https://www.wikihow.com/Upload-a-Website ""

Certainly! There are a few ways you can host a webpage for free and make it accessible via a link:

[1]: https://static.app/free-website-hosting ""

1. **Static.app**:
   - Static.app offers free HTML website hosting. You can upload your HTML website archive using their drag-and-drop interface, and they'll take care of displaying it online.
   - Your website will be up and running in moments, and they even include a free SSL certificate[^1^][1].

![GitHub Pages banner](https://www.bing.com/th?id=OSK.HEROPYXhmt9xIZFjih8rN47BRa4kK4GkSdxARfoD_7zE5s4&pid=cdx&w=200&h=128&c=7&rs=1)  

2. [**GitHub Pages**](https://careerfoundry.com/en/blog/web-development/how-to-host-a-website-for-free/):
   - If your website is based on HTML, CSS, and JavaScript, you can use GitHub Pages to host it for free.
   - Create a GitHub account, create a code repository, and upload your website files. GitHub Pages will automatically publish your site online[^2^][3].  

3. **FileZilla (FTP)**:
   - If you have your own domain and hosting, you can use an FTP program like FileZilla to upload your website files.
   - Connect to your hosting server using FTP credentials and upload your HTML files to the appropriate directory. 

![Canva Banner](https://www.bing.com/th?id=OSK.HEROG1NpexGAVRQF86DXRscedvTELmxtWTKie1rqFY5xvD4&pid=cdx&w=200&h=128&c=7&rs=1)  

4. [**Canva's Website Builder**](https://www.canva.com/website-builder/):
   - Canva offers a free website builder where you can publish your site with a my.canva.site domain or purchase a custom domain.
   - Enjoy worry-free web hosting, SSL certification, and WHOIS privacy protection[^3^][4].

Choose the option that best suits your needs, and you'll have your webpage accessible via a link in no time! 😊

Learn more: [1. static.app](https://static.app/free-website-hosting) 
[2. careerfoundry.com](https://careerfoundry.com/en/blog/web-development/how-to-host-a-website-for-free/) 
[3. www.canva.com](https://www.canva.com/website-builder/) 
[4. www.wikihow.com](https://www.wikihow.com/Upload-a-Website) 
[5. media.gettyimages.com](https://media.gettyimages.com/id/1211647318/photo/in-this-photo-illustration-a-github-logo-seen-displayed-on-a-smartphone.jpg?b=1&s=612x612&w=0&k=20&c=CojaA04sHzRcmXKYfY4X-GBg6u4yK7Fhx0KlECYnHtY=) 
[6. media.gettyimages.com](https://media.gettyimages.com/id/1972212744/photo/in-this-photo-illustration-a-canva-logo-seen-displayed-on-a.jpg?b=1&s=612x612&w=0&k=20&c=tTGB_UuUWnyFt7jv6k-NUpcyvgQxuIL8TQpEV_X03Z8=)  

*End of this Conversation*
