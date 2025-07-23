How to Setup Google Sites with Cloudflare
=========================================

>⚠️ Disclaimer: This guide is designed for users who are new to Google Sites and wish to set up a new site with a new domain using Cloudflare. It is intended for individuals who do not have pre-existing DNS settings or advanced configurations. If you already have custom DNS settings or are working with an existing configuration, this guide is not suitable. While configuring Cloudflare with Google Sites can improve your site's security and performance, incorrect settings can cause website disruptions, downtime, or data loss. Before you begin, make sure to back up any important information and, if necessary, seek professional assistance if you're unfamiliar with DNS settings or Cloudflare integration. Please note that the author cannot be held responsible for any issues, downtime, or data loss resulting from incorrect configurations or failure to follow the instructions in this guide. ***By proceeding, you do so at your own risk***.

This step-by-step guide walks you through setting up DNS settings, configuring HTTP to HTTPS redirects with page rules, and assigning your custom domain to your Google Sites project. Perfect for beginners, this guide covers everything from publishing your site to ensuring smooth performance and security. Set up your new site with Cloudflare and avoid common DNS configuration mistakes!

## Step 1: Purchasing the Domain

In order to setup Google Sites with Cloudflare, you must first purchase a domain from a registrar. In this setup guide, we will be using NameSilo.

1.  Navigate to [NameSilo.com](http://namesilo.com/).
2.  Type and search for the domain you'd like to purchase.
3.  Add the domain to cart and checkout.
4.  Select **Pay**.
    

## Step 2: Obtaining a Template
If you have your own, skip to the next step. In order to publish your Google Site, you need a template. KIRA INTERACTIVE offers free and premium Google Sites templates. 
1.  Navigate to [www.kirainteractive.com](http://www.kirainteractive.com/).
2.  Browse through the collection of free and premium sites. 
3.  To view a demo, select **VISIT DEMO**.
4.  When you are ready to purchase, select **PURCHASE**.
5.  Enter your payment details in the Stripe window and use promo code "THANKS5" for $5 off new customers.
6.  You should be prompted to download PDF with a link to the Google Drive where the template is stored.
7.  Sign-in to your Google account.
8.  Select **Copy Template** to copy the template to your personal Google Drive.
    

## Step 3: Pointing Domain to Cloudflare Nameservers
In order to use Cloudflare, you must point your new domain to Cloudflare's nameserver. 
1.  Sign-in to Cloudflare.
2.  In the left-hand pane, select **Account Home**.
3.  Select **Add a domain**.
4.  Type your domain name, toggle the **Manually enter DNS records** radio button, and select **Continue**.
5.  Select the Free plan and **Continue to activation**.
6.  Write down the unique nameservers Cloudflare provided.
7.  In a new tab, navigate back to [Namesilo.com](http://namesilo.com/).
8.  Select **My Account**.
9.  In the left-hand pane, select **Domain Manager**,
10.  Checkmark your domain and select **Change Nameservers**.
11.  Remove all nameserver entries, replace with Cloudflare's that were provided above, and Select **Submit**.
12.  Switch back to the Cloudflare tab and select **Continue**.
*NOTE: It may take up to 24 hours to switch.*

## Step 4: Removing Legacy DNS Entries From Namesilo
Cleanup time, you need to remove those legacy DNS entries from NameSilo.
1.  Navigate back to NameSilo.com.
2.  In the left-hand pane, select **Domain Manager**.
3.  Checkmark your domain and select the blue globe (**Manage DNS settings for this domain**).
4.  Delete all your DNS entries.
    

## Step 5: Publishing Your Google Site & Assigning Property Authority 

Google Sites requires you to confirm you own the domain (aka "Property").
1.  Sign-in to your Google account, navigate to your Google Site page and select **Publish**.
2.  In the bottom of the new window, under "Who can view my site", select **MANAGE**.
3.  Next to "Published site", toggle **Public**.
4.  Type an address you'd like Google to internally view your website at (not your domain).
5.  Select **Use my existing domain**.
6.  Select **Connect Domain** (a new Google Search Console tab should appear).
7.  Leave the "www" prefix and type your domain.
8.  Select **Verify your ownership**.
9.  Ensure your purchased domain is spelled correctly, and select **Continue**.
10.  Select **START VERIFICATION** (Google will ask you to sign-in to your Cloudflare account).
11.  Select **Authorize** to add the TXT entry to your DNS settings.
12.  Switch back to your Google Search Console tab.
13.  Now that you authorized your domain, select **Next** (if everything is properly authorized, Google Search Console will congratulate you).
14.  Switch back to your Google Sites tab, and select **Done** and **Publish**.
    
## Step 6: Configuring DNS & Naked Domain Redirect
Now it's time to point your domain (www) and naked domain (without www) to Google Sites servers.
1.  Navigate to CloudFlare.com and sign-in.
2.  In the left hand pane, select **DNS**.
3.  Select **Add Record** and create two new records with the following settings:
```
TYPE       Name      Target                  Proxy Status Note
CNAME      www       ghs.googlehosted.com    Proxied www.<yourdomain>.com
CNAME      @         ghs.google.com          Proxied <yourdomain>.com, aka "naked" domain
```

*NOTE: This step takes at least 1 hour. If you try to visit your domain now, you will receive "SSL handshake" errors. Just go for a walk and come back.*

## Step 7: HTTP to HTTPS Redirect
Now you need to redirect all traffic to your domain and naked domain to use HTTPS.
1.  Navigate to CloudFlare.com and sign-in.  
2.  In the left hand pane, select **Rules | Page Rules**.   
3.  Select, **Create Page Rule** and with the following settings:
```
URL                        Pick a Setting        Select a Status Code        Enter Destination
<yourdomain>.com/\*CNAME   Fowarding URL         302 - Temporary Redirect    https://www.<yourdomain>.com/$1
```
4.  Select, **Save and Deploy Page Rule**.

*NOTE: You should be able to type just `<yourdomain>.com` instead of `www.<yourdomain>.com`. Also, you should be using HTTPS.*

## Step 8: Getting Listed on Google
Great, your site is published! Now it's time to get your website listed on Google.
1.  Navigate to the Google Search Console at [https://search.google.com/search-console/about](https://search.google.com/search-console/about). 
2.  Select **Start now**.
3.  In the left hand pane, select **URL inspection**.
4.  Type your domain into the inspection field.
5.  Select, **REQUEST INDEXING**.
6.  Repeat steps 3-5 of this section for every page of your website.
    
Need more help with Google Sites? KIRA INTERACTIVE LLC specializes in migrating outdated websites, designing custom pages, configuring DNS settings, setting up email, and aligning your site with your unique branding and aesthetic. Whether you're a business, school, or nonprofit, we build clean, modern, and fully functional websites tailored to your needs—fast, polished, and professional. Book your consultation today and launch with confidence.
