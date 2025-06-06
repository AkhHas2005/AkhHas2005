# Troubleshooting AI Search Web App Issues

## Me
I have an AI search web app developed with Google Vertex AI Agent builder, however the serach starts generating the summary but then goes blank and doesn't show anything except the search results  

## Co-Pilot
[1]: https://cloud.google.com/generative-ai-app-builder/docs/get-search-summaries ""
[2]: https://www.pondhouse-data.com/blog/what-is-vertex-ai-agent-builder ""
[3]: https://cloud.google.com/generative-ai-app-builder/docs/preview-search-results ""

It seems like you're encountering an issue with your AI search web app developed using Google Vertex AI Agent Builder. Let's troubleshoot this together! 😊

First, let's ensure that you're following the correct steps to get search summaries. Here's how you can do it:

1. **Turn on Advanced LLM Features:**
   - If you have an unstructured search app, make sure you've enabled the Advanced LLM features.
   - For a website search app, turn on the following features:
     - Enterprise edition features.
     - Advanced LLM features.
     - Advanced website indexing (requires domain verification).

2. **Get a Search Summary:**
   - A search summary is a short summarization of the top search results returned in a search response.
   - To get a summary, you must also get extractive answers with your search results. You can specify the number of top results to generate the search summary from.
   - For example, in your search request, include the following:
     ```json
     "contentSearchSpec": {
       "summarySpec": {
         "summaryResultCount": 3
       },
       "extractiveContentSpec": {
         "maxExtractiveAnswerCount": 1
       }
     }
     ```
     Adjust the values as needed for your use case.

3. **Markdown Rendering:**
   - Search summaries can include Markdown-formatted text. Consider using a Markdown parser in your application to render Markdown text.

4. **Check LLM Models:**
   - If you notice differences between console results and API results, it might be due to different LLM models being used. The console typically uses a stable LLM model.

Remember to verify your app settings and ensure that you're correctly handling the summary content. If you encounter any further issues, feel free to ask for more assistance! 🚀

For more detailed information, you can refer to the [official documentation](https://cloud.google.com/generative-ai-app-builder/docs/get-search-summaries).[^1^][1] And if you'd like to explore what Vertex AI Agent Builder offers, it's a platform that helps developers build and deploy AI agents, regardless of their expertise level. It provides both a no-code console and open-source frameworks for more advanced development[^2^][2]. 😊

Learn more: [1. cloud.google.com](https://cloud.google.com/generative-ai-app-builder/docs/get-search-summaries) 
[2. www.pondhouse-data.com](https://www.pondhouse-data.com/blog/what-is-vertex-ai-agent-builder) 
[3. cloud.google.com](https://cloud.google.com/generative-ai-app-builder/docs/preview-search-results)  

## Me
I've checked the settings, but it's still not working.  

## Co-Pilot
I apologize for the inconvenience you're experiencing. Let's explore some additional troubleshooting steps:

1. **Logs and Errors:**
   - Check your application logs or console for any error messages or warnings related to the search functionality. Sometimes, specific issues might be logged there.
   - If you find any relevant error messages, please share them with me so that I can provide more targeted assistance.

2. **API Response Inspection:**
   - When you make a search request, inspect the API response carefully. Ensure that the search results are being returned correctly.
   - Specifically, check if the search summary content is included in the response payload.
   - If you're using a programming language or SDK to make the API call, verify that you're correctly extracting the summary content from the response.

3. **Rate Limits and Quotas:**
   - Confirm that you're not hitting any rate limits or quotas imposed by the Google Vertex AI service. Sometimes, exceeding these limits can cause unexpected behavior.
   - Review your project's quotas and ensure that you're within the allowed limits.

4. **Content Source and Indexing:**
   - Verify that the content source (e.g., website, documents, etc.) you're searching against is correctly indexed.
   - If you're using a custom data source, ensure that it's properly configured and up-to-date.

5. **Test with Different Queries:**
   - Try different search queries to see if the issue persists across various search terms.
   - Sometimes, specific queries may trigger unexpected behavior due to the content or indexing.

6. **Caching and Refresh:**
   - Clear any caches related to your search results or summaries.
   - If your app caches search results, it might be serving outdated content.

7. **Contact Support:**
   - If none of the above steps resolve the issue, consider reaching out to Google Cloud support. They can provide more specific guidance based on your project setup.

Remember that debugging can be a process of elimination, so take your time and systematically check each aspect. If you encounter any specific error messages or need further assistance, feel free to share more details, and I'll do my best to help! 🛠️🔍  

## Me
It's not even genrating the summary on the agent builder?  

## Co-Pilot
I apologize for the inconvenience you're facing. If the search summary isn't generating within the Vertex AI Agent Builder, let's explore some additional steps:

1. **Check Data Sources:**
   - Ensure that your data sources (websites, documents, etc.) are correctly configured and indexed.
   - Verify that the content you're searching against is accessible and up-to-date.

2. **Review Search Configuration:**
   - Double-check your search configuration settings within the Agent Builder.
   - Confirm that you've enabled the necessary features for search summaries (Advanced LLM features, extractive answers, etc.).

3. **Test with Different Queries:**
   - Try different search queries to see if the issue persists across various terms.
   - Sometimes, specific queries may behave differently due to content or indexing.

4. **Inspect Logs:**
   - Look for any error messages or warnings related to search functionality in your application logs or console.
   - If you find any relevant logs, share them for further analysis.

5. **Rate Limits and Quotas:**
   - Ensure that you're not exceeding any rate limits or quotas imposed by Vertex AI.
   - Review your project's quotas and usage.

6. **Contact Support:**
   - If the issue persists, consider reaching out to Google Cloud support. They can provide specific guidance based on your setup.

Remember that debugging can be a process of elimination. Take your time, and we'll work through this together! 🛠️🔍  

## Me
I'm getting these error messages:  
Failed to load resource: the server responded with a status of 404 () discoveryengine.clients6.google.com/v1alpha/projects/bcft-429709/locations/global/collections/default_collection/dataStores/ehm-user-guides_1721214296548?key=AIzaSyCI-zsRP85UVOi0DjtiCwWBwQ1djDy741g:1  
Failed to load resource: the server responded with a status of 404 () discoveryengine.clients6.google.com/v1alpha/projects/bcft-429709/locations/global/collections/default_collection/dataStores/ehm-user-guides_1721214296548?key=AIzaSyCI-zsRP85UVOi0DjtiCwWBwQ1djDy741g:1  
Failed to load resource: the server responded with a status of 404 () 2m=core:3654 No ID or name found in config. _.h.updateJsLog @ m=core:3654 discoveryengine.clients6.google.com/v1alpha/projects/bcft-429709/locations/global/collections/default_collection/dataStores/ehm-user-guides_1721214296548?key=AIzaSyCI-zsRP85UVOi0DjtiCwWBwQ1djDy741g:1  
Failed to load resource: the server responded with a status of 404 () 2m=core:3654 No ID or name found in config. _.h.updateJsLog @ m=core:3654 discoveryengine.clients6.google.com/v1alpha/projects/bcft-429709/locations/global/collections/default_collection/dataStores/ehm-user-guides_1721214296548?key=AIzaSyCI-zsRP85UVOi0DjtiCwWBwQ1djDy741g:1  
Failed to load resource: the server responded with a status of 404 () 2m=core:3654 No ID or name found in config. _.h.updateJsLog @ m=core:3654 discoveryengine.clients6.google.com/v1alpha/projects/bcft-429709/locations/global/collections/default_collection/dataStores/ehm-user-guides_1721214296548?key=AIzaSyCI-zsRP85UVOi0DjtiCwWBwQ1djDy741g:1  
Failed to load resource: the server responded with a status of 404 () default_search:answer:1  
Failed to load resource: the server responded with a status of 403 () 1000Third-party cookie will be blocked in future Chrome versions as part of Privacy Sandbox. default_search:answer:1  
Failed to load resource: the server responded with a status of 403 () m=core:269  
POST https://discoveryengine.clients6.google.com/v1alpha/projects/545020189115/locations/global/collections/default_collection/engines/ehm-user-guides_1721214296548/servingConfigs/default_search:answer?key=AIzaSyCI-zsRP85UVOi0DjtiCwWBwQ1djDy741g 403 (Forbidden)  

## Co-Pilot
Thank you for sharing the error messages. Let's address each issue step by step:

1. **404 Errors:**
   - The "404" status code indicates that the requested resource (URL) was not found on the server.
   - In your case, it seems that the URLs related to the data store (`ehm-user-guides_1721214296548`) are returning a 404 error.
   - Verify that the data store exists and is correctly configured within your application.

2. **403 Errors:**
   - The "403" status code indicates a forbidden access error. It means that the server understood the request, but the user does not have permission to access the requested resource.
   - Check the following:
     - Ensure that your API key (`AIzaSyCI-zsRP85UVOi0DjtiCwWBwQ1djDy741g`) is valid and has the necessary permissions.
     - Confirm that the project ID (`bcft-429709`) and other identifiers are correctly specified.
     - Review your access controls and permissions for the data store and search engine.

3. **No ID or Name Found in Config:**
   - This message suggests that there might be an issue with the configuration settings.
   - Double-check your configuration files or settings within the Vertex AI Agent Builder.
   - Ensure that all required fields (such as project ID, collection names, and data store IDs) are correctly specified.

4. **Third-Party Cookie Warning:**
   - The warning about third-party cookies being blocked is related to browser security settings.
   - While this warning doesn't directly impact your search functionality, it's good to be aware of it.
   - Make sure your application handles cookies appropriately.

5. **Rate Limits and Quotas:**
   - Confirm that you're not exceeding any rate limits or quotas imposed by Google Cloud.
   - Review your project's quotas and usage.

6. **Contact Support:**
   - If the issue persists, consider reaching out to Google Cloud support. They can provide specific guidance based on your setup.

Remember that debugging can be a process of elimination. Take your time, and let's work through these issues together. If you need further assistance or encounter any other errors, feel free to share more details! 🛠️🔍  

## Me
What could be the reason for these 2 errors in the con text of the AI serach preview through agent builder:   
POST https://discoveryengine.clients6.google.com/v1alpha/projects/545020189115/locations/global/collections/default_collection/engines/ehm-user-guides_1721214296548/servingConfigs/default_search:answer?key=AIzaSyCI-zsRP85UVOi0DjtiCwWBwQ1djDy741g 403 (Forbidden)  
POST https://cloud.google.com/ai/gen-app-builder/_/UcsWidgetPreviewUi/jserror?script=https%3A%2F%2Fcloud.google.com%2Fai%2Fgen-app-builder%2Fconsole-preview%2Fsearch%3Forigin%3Dconsole.cloud.google.com%26hl%3Den_GB&error=ErrorResponse%3A%20%7B%22errorParameters%22%3A%7B%22map%22%3A%7B%7D%7D%2C%22url%22%3A%22https%3A%2F%2Fdiscoveryengine.clients6.google.com%2Fv1alpha%2Fprojects%2F545020189115%2Flocations%2Fglobal%2Fcollections%2Fdefault_collection%2Fengines%2Fehm-user-guides_1721214296548%2FservingConfigs%2Fdefault_search%3Aanswer%3Fkey%3DAIzaSyCI-zsRP85UVOi0DjtiCwWBwQ1djDy741g%22%2C%22headers%22%3A%7B%7D%2C%22status%22%3A403%2C%22statusText%22%3A%22OK%22%2C%22method%22%3A%22POST%22%2C%22body%22%3A%7B%22error%22%3A%7B%22code%22%3A403%2C%22message%22%3A%22The%20caller%20does%20not%20have%20permission%22%2C%22status%22%3A%22PERMISSION_DENIED%22%7D%7D%2C%22bodyText%22%3A%22%7B%5C%22error%5C%22%3A%7B%5C%22code%5C%22%3A403%2C%5C%22message%5C%22%3A%5C%22The%20caller%20does%20not%20have%20permission%5C%22%2C%5C%22status%5C%22%3A%5C%22PERMISSION_DENIED%5C%22%7D%7D%22%2C%22errorExperience%22%3A1%2C%22clientHandler%22%3A0%2C%22trackingId%22%3A%22c321809369365347%22%2C%22message%22%3A%22The%20caller%20does%20not%20have%20permission%22%2C%22errorCode%22%3A403%7D&line=Not%20available 502 (Bad Gateway)  

## Co-Pilot
[1]: https://cloud.google.com/generative-ai-app-builder/docs/get-search-summaries ""
[2]: https://cloud.google.com/generative-ai-app-builder/docs/generic-search-checklist ""
[3]: https://www.pondhouse-data.com/blog/what-is-vertex-ai-agent-builder ""
[4]: https://cloud.google.com/generative-ai-app-builder/docs/preview-search-results ""
[5]: https://cloud.google.com/vertex-ai/docs/general/troubleshooting-workbench ""
[6]: https://stackoverflow.com/questions/78176807/title-403-permission-denied-error-when-accessing-google-ai-platform-model ""
[7]: https://stackoverflow.com/questions/78539855/getting-configuration-is-not-authorized-error-while-deploying-gcp-vertex-ai-ag ""

The errors you're encountering in the context of the AI search preview through Agent Builder indicate permission-related issues. Let's break down each error:

1. **403 Forbidden Error**:
   - The first error occurs when making a request to the following URL:
     ```
     POST https://discoveryengine.clients6.google.com/v1alpha/projects/545020189115/locations/global/collections/default_collection/engines/ehm-user-guides_1721214296548/servingConfigs/default_search:answer?key=AIzaSyCI-zsRP85UVOi0DjtiCwWBwQ1djDy741g
     ```
   - The error message states: "The caller does not have permission."
   - This typically means that the user or service account making the request lacks the necessary permissions to access the specified resource.
   - To resolve this, ensure that the account has appropriate permissions for the Vertex AI Agent Builder and related services.

2. **502 Bad Gateway Error**:
   - The second error occurs when accessing the following URL:
     ```
     POST https://cloud.google.com/ai/gen-app-builder/_/UcsWidgetPreviewUi/jserror?script=https%3A%2F%2Fcloud.google.com%2Fai%2Fgen-app-builder%2Fconsole-preview%2Fsearch%3Forigin%3Dconsole.cloud.google.com%26hl%3Den_GB&error=ErrorResponse%3A%20%7B%22errorParameters%22%3A%7B%22map%22%3A%7B%7D%7D%2C%22url%22%3A%22https%3A%2F%2Fdiscoveryengine.clients6.google.com%2Fv1alpha%2Fprojects%2F545020189115%2Flocations%2Fglobal%2Fcollections%2Fdefault_collection%2Fengines%2Fehm-user-guides_1721214296548%2FservingConfigs%2Fdefault_search%3Aanswer%3Fkey%3DAIzaSyCI-zsRP85UVOi0DjtiCwWBwQ1djDy741g%22%2C%22headers%22%3A%7B%7D%2C%22status%22%3A403%2C%22statusText%22%3A%22OK%22%2C%22method%22%3A%22POST%22%2C%22body%22%3A%7B%22error%22%3A%7B%22code%22%3A403%2C%22message%22%3A%22The%20caller%20does%20not%20have%20permission%22%2C%22status%22%3A%22PERMISSION_DENIED%22%7D%7D%2C%22bodyText%22%3A%22%7B%5C%22error%5C%22%3A%7B%5C%22code%5C%22%3A403%2C%5C%22message%5C%22%3A%5C%22The%20caller%20does%20not%20have%20permission%5C%22%2C%5C%22status%5C%22%3A%5C%22PERMISSION_DENIED%5C%22%7D%7D%22%2C%22errorExperience%22%3A1%2C%22clientHandler%22%3A0%2C%22trackingId%22%3A%22c321809369365347%22%2C%22message%22%3A%22The%20caller%20does%20not%20have%20permission%22%2C%22errorCode%22%3A403%7D&line=Not%20available
     ```
   - Again, the error message indicates a permission issue: "The caller does not have permission."
   - Verify that the service account or user making the request has the necessary permissions to access the resources involved.

To address these errors:
- Check the permissions associated with your service account or user.
- Ensure that the necessary roles (such as Vertex AI User) are granted.
- Verify that the authorized domains/subdomains are correctly configured if applicable.

If the issue persists, consider reaching out to Google Cloud support for more specific guidance based on your setup. 🛠️🔍[^1^][6] [^2^][7]

Learn more: [1. stackoverflow.com](https://stackoverflow.com/questions/78176807/title-403-permission-denied-error-when-accessing-google-ai-platform-model) 
[2. stackoverflow.com](https://stackoverflow.com/questions/78539855/getting-configuration-is-not-authorized-error-while-deploying-gcp-vertex-ai-ag) 
[3. cloud.google.com](https://cloud.google.com/generative-ai-app-builder/docs/get-search-summaries) 
[4. cloud.google.com](https://cloud.google.com/generative-ai-app-builder/docs/generic-search-checklist) 
[5. www.pondhouse-data.com](https://www.pondhouse-data.com/blog/what-is-vertex-ai-agent-builder) 
[6. cloud.google.com](https://cloud.google.com/generative-ai-app-builder/docs/preview-search-results) 
[7. cloud.google.com](https://cloud.google.com/vertex-ai/docs/general/troubleshooting-workbench)  

*End of this Conversation*
