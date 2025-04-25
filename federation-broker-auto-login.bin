// ==UserScript==
// @name         Federation Broker Auto-Login
// @description  Automatically clicks on SAML login link for the specified user
// @version      0.0.1
//
// @namespace    glucose.stream
// @author       glucose.stream
// @supportURL   mailto:userscript@glucose.stream
//
// @match        https://federationbroker.cloudflareaccess.com/cdn-cgi/access/login/*
// @grant        GM_getValue
// ==/UserScript==

(function() {
    'use strict';

    let nameFromStore = GM_getValue("name", "")

    // Get the name from the userscript settings and error if not a string
    if (nameFromStore === "") {
      console.log("Userscript variable 'name' not set or empty!");
      return false;
    }

   var titleToMatch = `SAML ・ ${nameFromStore}`;

    // Function to find and click the SAML link
    function findAndClickSamlLink() {
        // Look for all divs with the AuthServiceLogin-row class
        const loginRows = document.querySelectorAll('div.AuthServiceLogin-row');

        // Loop through each row
        for (const row of loginRows) {
            // Find anchor elements within each row
            const anchors = row.querySelectorAll('a');

            // Check each anchor for the specific title
            for (const anchor of anchors) {
                if (anchor.title === titleToMatch) {
                    console.log(`Found SAML login link for ${nameFromStore}, clicking it...`);
                    // Click the link
                    anchor.click();
                    return true;
                }
            }
        }

        // If we reach here, no matching link was found
        console.log(`SAML login link for ${nameFromStore} not found`);
        return false;
    }

    // Execute when the page is fully loaded
    window.addEventListener('load', function() {
        findAndClickSamlLink();
    });

})();
