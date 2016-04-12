---
title: Privacy
layout: page
jumbotron:
  title: Privacy
---

# Privacy Statement and Disclosure

__Webgroup Media LLC (WGM)__ is a commercial open source company that has been leading and supporting the community development of Cerb since January 2002. In connection with this business, we operate the [cerberusweb.com](http://cerberusweb.com) project website, as well as an On-Demand ("software as a service") network of applications hosted by subscription as subdomains of the cerb.me domain.

It is WGM's policy to respect your privacy regarding any information we may collect while operating our websites and services. We do not sell any personally identifiable information or data stored by On-Demand services to third-parties. We do not directly share your information with third-parties without explicit permission except to comply with the law or to provide necessary infrastructure in connection with the services you request; however, there is some passive risk of exposure to third-party access inherent in web-based services that is outlined in detail below. We do our best to mitigate and minimize these risks on your behalf.

## Website Visitors

Like most website operators, WGM collects non-personally identifying information of the sort that web browsers and servers typically make available, such as the browser type, language preference, referring site, and the date and time of each visitor request. WGM's purpose in collecting non-personally identifying information is to better understand how WGM's visitors use its website. From time to time, WGM may release non-personally identifying information in the aggregate; e.g., by publishing a report on trends in the usage of its website.

WGM also collects potentially personally identifying information like Internet Protocol (IP) addresses for website visitors and workers. WGM only discloses IP addresses under the same circumstances that it uses and discloses personally identifying information as described below.

## Gathering of Personally Identifying Information

Certain visitors to WGM's websites choose to interact in ways that require us to gather personally identifying information. The amount and type of information that WGM gathers depends on the nature of the interaction. For example, we ask workers who sign up for On-Demand services to provide an email address. Those who engage in financial transactions with WGM (e.g. by purchasing products and services) are asked to provide additional information, including as necessary the personal and financial information required to process those transactions. In each case, WGM collects such information only insofar as is necessary or appropriate to fulfill the purpose of the visitor's interaction with WGM. WGM does not disclose personally identifying information other than as described below. Visitors can always refuse to supply personally identifying information, with the caveat that it may prevent them from purchasing or engaging in certain services.

## Aggregated Statistics

WGM may collect statistics about the behavior of visitors to its websites or workers of its On-Demand software. For instance, WGM may gather metrics about individual Cerb instances like the number of workers, addresses, conversations, messages, and attachments; the composition of file attachments such as distributions of sizes or file types; or the amount of activity over a given time period. This information is used to improve the usability and performance of products and services provided by WGM.

WGM may display this aggregate, anonymous information publicly or provide it to others. However, WGM does not disclose personally identifying information other than as described below.

## Protection of Certain Personally Identifying Information

WGM discloses personally identifying information only to those of its employees, contractors and affiliated organizations that (i) need to know that information in order to process it on WGM's behalf or to provide products and services available at WGM's websites, and (ii) that have agreed not to disclose it to others. Some of those employees, contractors, and affiliated organizations may be located outside of your home country; and by using WGM's websites, you consent to the transfer of such information to them. WGM will not rent or sell potentially personally identifying and personally identifying information to anyone. Other than to its employees, contractors and affiliated organizations, as described above, WGM discloses personally identifying information only in response to a subpoena, court order, or other governmental request, or when WGM believes in good faith that disclosure is reasonably necessary to protect the property or rights of WGM, third parties, or the public at large.

If you are a registered user of a WGM product or service like Cerb and have supplied your email address, WGM may occasionally send you an email to tell you about new features or to solicit your feedback. We primarily use our social network profiles to communicate this type of information, and we expect to keep email broadcasts to a minimum. If you send us a request (e.g. via a support email or one of our feedback mechanisms), we reserve the right to anonymously republish it in order to help us clarify or respond to your request, or to help us support other users. WGM takes all measures reasonably necessary to protect against the unauthorized access, use, alteration or destruction of potentially personally identifying information.

## Security and Safeguards

WGM takes reasonable precautions to protect your data and personally identifying information.

We do not have physical access to any of our servers or online storage mediums.  See the section about "Third-Party Data Centers" for the upstream security policies of SoftLayer, Amazon Web Services, and Linode.  These servers are protected within state-of-the-art data centers.

WGM performs 24/7/365 monitoring of our network and service infrastructure.  This includes metrics like server load, process information, account access, service utilization, and network activity.

Web-based communication with our servers is protected through 256-bit encryption via Secure Socket Layer (SSL) technology. This feature is included with all On-Demand applications when URLs are prefixed with "https://".  It is the responsibility of clients and their representatives to ensure the use of SSL; and upon request we can configure your application to require the use of SSL.

We do not store credit card information on our servers.  For one-time transactions we do not save credit card or bank account numbers anywhere, although we do store email-based receipts that include contact information, payment type, transaction IDs, and authorization codes.  For recurring transactions, payment information is stored with vendors who adhere to the Payment Card Industry Data Security Standards (PCI DSS).  We use [FreshBooks](http://www.freshbooks.com>) for sending invoices and collecting payments, and they protect financial information with AES encryption.  We process credit card transactions through our merchant account at Authorize.net.  Depending on a client's preferred payment method, these transactions may alternatively take place through other vendors like PayPal, or through wire transfers to Wells Fargo Bank.  We do not have access to client credit card numbers or bank account information through any of these vendors.

WGM technicians securely access our servers using Secure Shell (SSH) encryption.  Logins are authenticated with [RSA keys](http://en.wikipedia.org/wiki/RSA_(algorithm)) rather than simple passwords.  We do not provide general purpose client access (e.g. SSH, Telnet, FTP) to machines housing multi-tenant On-Demand data.

We have disabled insecure features in our PHP environment (e.g. process control, shell command execution, remote file includes) to protect against arbitrary code execution.  To protect against cross-site scripting (XSS), we "[escape](http://en.wikipedia.org/wiki/HTML#Character_and_entity_references>)" all user-provided data that is displayed in a web browser.

## Disclosure of Security Breaches

WGM will notify you as soon as possible if a security breach results in the potential disclosure of any personally identifiable information or data related to your account. At the conclusion of a security investigation, WGM will provide you with a report about the nature of any compromised data (e.g. email addresses, worker account passwords) and the actions taken to prevent future intrusions.

## Third-Party Data Centers, Cloud Computing, and Virtualization

WGM remotely provisions, administers, and maintains servers in various data centers throughout the world and WGM does not maintain a physical presence in any of them. Most On-Demand services are currently provided from machines exclusively leased and operated by WGM from SoftLayer in their Seattle and Dallas facilities. However, other services, like our project portal, are provided from virtual servers in cloud computing and storage environments at Amazon Web Services, Linode, and Slicehost (Rackspace Cloud). In virtual environments, many users from various organizations share a pool of resources like computational power and storage capacity, although provisioned resources are isolated from one another to a similar degree as leased machines in a datacenter.

Due to the remote nature of leased servers, colocation, cloud computing, and virtualization, authorized technicians from our vendors and service providers may have temporary access to our servers in order to perform physical maintenance and upgrades, or to provide hands-on assistance with troubleshooting issues like RAID degradation and hardware failures.

In such events we defer to upstream privacy policies:

-  <https://aws.amazon.com/privacy>
-  <http://www.softlayer.com/privacy-agreement>
-  <https://www.linode.com/privacy>

## Backups

Cerb has two main components for storing customer data: (1) the database, and (2) the /storage/ filesystem which contains large, immutable content like email attachments. Data may be stored on a single machine, or distributed among several machines, on our On-Demand network. Generally, that data will be housed on WGM's dedicated servers in SoftLayer's datacenters.

If you communicate with WGM, or use On-Demand services provided by WGM, your information will be regularly copied for the express purpose of maintaining backups for continuity and disaster recovery. Nightly backups and redundant storage are kept on machines controlled remotely by WGM. Backups may be transferred to Amazon's Simple Storage Service (S3) for long-term, off-site archival.

When WGM runs nightly backups, we make full backups of the database, and incremental backups of the /storage/ filesystem.  These are stored in the same datacenter, and are often attached to the same server, but on an alternate, redundant storage medium.

Twice per week (usually Wednesday and Sunday) we off-site the latest backups to our private buckets on Amazon's S3 service.  We also rotate these to keep a weekly backup for a few months of history, and at least the most recent three backups.

## Disposal of Data and Backups

Upon cancellation, we remove all client data from the On-Demand network and send a final backup to Amazon S3.  We will attempt to make arrangements for this backup to be transferred to the client before permanently destroying our copies of the data.  Without an explicit request for their immediate removal, backups may be persisted for several months.

We will comply with any written, and duly authenticated, client requests for the immediate destruction of all account data and backups.

## Testimonials

WGM displays a list of clients and testimonials on our websites. We do not disclose the names of licensed organizations, or their representatives, without explicit permission, except in the event that a client freely discloses their identity through postings on public forums or social networks.

## Cookies

A cookie is a string of information that a website stores on a visitor's computer, and that the visitor's browser provides to the website each time the visitor returns. WGM uses cookies to help WGM identify and track visitors, their usage of WGM website, and their website access preferences. Visitors who do not wish to have cookies placed on their computers should set their browsers to refuse cookies before using WGM's websites, with the drawback that certain features of WGM's websites may not function properly without the aid of cookies. Web-based products like Cerb require cookies to be enabled, although their use is limited to maintaining a logged-in session within the software.

## Business Transfers

If WGM, or substantially all of its assets were acquired, or in the unlikely event that WGM goes out of business or enters bankruptcy, user information would be one of the assets that is transferred or acquired by a third party. You acknowledge that such transfers may occur, and that any acquirer of WGM may continue to use your personal information as set forth in this policy.

## Ads

In the rare event that ads appear in any of our applications or on any of our websites, they may be delivered to users by advertising partners, who may set cookies. These cookies allow the ad server to recognize your computer each time they send you an online advertisement to compile information about you or others who use your computer. This information allows ad networks to, among other things, deliver targeted advertisements that they believe will be of most interest to you. This Privacy Policy covers the use of cookies by WGM and does not cover the use of cookies by any advertisers.

## Privacy Policy Changes

Although most changes are likely to be minor, WGM may change its Privacy Policy from time to time, and in WGM's sole discretion. WGM encourages visitors to frequently check this page for any changes to its Privacy Policy. Your continued use of this site after any change in this Privacy Policy will constitute your acceptance of such change.

## License

This privacy policy is available under a [Creative Commons Sharealike](http://creativecommons.org/licenses/by-sa/2.5/) license derived from original groundwork by [Automattic](http://automattic.com/privacy/). WGM has no professional affiliation with Automattic.
