# SCaLE20x: Repodiving into Open Source at CMS.gov
https://www.socallinuxexpo.org/scale/20x/presentations/repodiving-open-source-cmsgov


## INTRO TO DIGITAL SERVICE AT CMS (DSAC)
My name is Remy DeCausemaker, my pronouns are he/him, and I'm the Open Source
Lead at the Digital Service at the Centers for Medicare & Medicaid Services
(CMS.) Before I get started, tho, a few standard disclaimers:

*The views presented here today are those of the speaker and do not necessarily
represent the views of CMS, it's components, or any other components of the
United States Federal Government.*

*I am not a lawyer or an accountant, and this presentation does not constitute
legal or financial advice.*

Now then :P

The Digital Service works to transform the U.S. Healthcare system by improving
the design of healthcare experiences, delivering value to government,
providers, and patients, modernizing systems, and participating in policy
development. We accomplish this by deploying small responsive groups of
designers, engineers, and product managers within CMS on a 'tour of duty' to
work alongside dedicated civil servants. These multidisciplinary teams bring
best practices and new approaches to support government modernization efforts, and 
solve some of the most complex problems facing our healthcare system today.

## Gource
This video you're seeing is a Gource visualization of CMS Open API source code
repositories created by developers at the Centers for Medicare and Medicaid
Services (CMS.gov), and maintained by the Office of Enterprise Data and
Analytics (OEDA.)

Software projects are displayed by Gource as animated trees, where directories
appear as branches, and files appear as leaves of bubbles. Developers are seen
working on the trees at the times they contributed to the project, where red
lazers are deletions, green lazers are additions, and orange lazers are edits. 

I have color-coded each repo, so that each colored tree represents one project.


## The Gource Process
1. Install dependencies
2. Create repos directory
3. Clone repos
4. Generate logs
5. Insert parent names
6. Colorize logs
7. Concatenate and sort logs
8. Run Gource 
9. Export video


We'll dig into the config and rendering pipelines a bit later in the presentation.
For now, let's talk about WHAT repos you are looking at ;)

## https://Developer.CMS.gov
[Developer.CMS.gov](https://developer.cms.gov) contains CMS' collection of
APIs, datasets, frameworks, and style guides to develop applications that help
people get the services and benefits they rely on.

All repos seen in this video can be found via that website (which links to
https://github.com/cmsgov when repos are public.)

### The 5 specific repos we're visualizing today are:

#### 1) Beneficiary FHIR Data (BFD) Server 
BFD Server is an internal backend to Medicare beneficiaries' demographic,
enrollment, and claims data in FHIR format

FHIR stands for Fast Healthcare Interoperability Resource, and v1 development
began in 2012, and current version is up to v4. It is an Open Standard that
defines how healthcare information can be exchanged between different computer
systems regardless of how it is stored in those systems. 

It allows healthcare information, including clinical and administrative data,
to be available securely to those who have a need to access it, and to those
who have the right to do so for the benefit of a patient receiving care. The
standards development organization HL7® (Health Level Seven®) uses a
collaborative approach to develop and upgrade FHIR.[1](https://www.healthit.gov/sites/default/files/2019-08/ONCFHIRFSWhatIsFHIR.pdf)

FHIR is RESTful, meaning that it server will respond with the representation of
a resource (most often be an HTML, XML or JSON document) and that resource will
contain hypermedia links that can be followed to make the state of the system
change.[2](https://en.wikipedia.org/wiki/Representational_state_transfer)

*tl;dr, it allows clinical and administrative data about healthcare records to
be encoded into structured data, and wrapped in a RESTful API.*


#### 2) Beneficiary Claims Data API (BCDA)
enables ACCOUNTABLE CARE ORGANIZATIONS (ACOs) to retrieve Medicare Part A/B/D claims data for beneficiaries.

*tl;dr - BFD is the backend that powers specific APIs that deliver claims and records to
different types of users within healthcare.* 

#### 3) Data-at-the-point-of-care (DPC) API 
enables making a patient's Medicare claims data available to HEALTH CARE PROVIDERS for treatment purposes

#### 4) AB2D API Development Begins - https://github.com/CMSgov/ab2d
provides Prescription Drug Sponsors with secure Medicare parts A and B claims data for their plan enrollees

#### 5) BlueButton 2.0 API
delivers Medicare Part A, B, and D data for over 60 million people with Medicare.
Bluebutton is probably our most widely used and longest lived Open API projects.


### BlueButton Brief Timeline
- May 2015 - Project Begins
- March 2018 - Public Launch
- May 2020 - Interoperability and Patient Access final rule published, with enforcement starting July 2021
- November 2020 - CARIN Blue Button FHIR Implementation Guide v1.0 released


### How CMS is enabling data exchange
- CMS collaborates with the industry, implements programs, and develops
policies to support interoperability in the U.S. health care system with
human-centered design in mind.

- Since March 2018, CMS, in collaboration with CARIN (a multi-sector group of
stakeholders representing numerous hospitals, thousands of physicians and
clinicians, and millions of patients and other consumers and caregivers.),
launched FHIR-enabled Blue Button 2.0 which provides Medicare Parts A, B, and D
claims and enrollment data for one individual person with Medicare at a time to
registered applications with authorization.

- In May 2020, CMS published the Interoperability and Patient Access final rule (CMS-9115-F)
which puts patients first by establishing policies that break down barriers in the nation’s
health system to enable better patient access to their health information, improve
interoperability and unleash innovation, while reducing burden on payers and providers.

- Together, Blue Button 2.0 and the Interoperability and Patient Access final rule
establish policies and implement data exchange capabilities aimed at:
    - Enabling better patient access to their health information;
    - Improving interoperability across the health care system;
    - Unleashing innovation, and;
    - Reducing administrative burden on payers and providers.


## Gource Configuration file Walkthrough
See: https://github.com/decause-gov/cms-gource/blob/main/cms.conf

## CONCLUSION

There are hundreds of repos, thousands of contributors, and millions of lines
of code.

There are repos to contribute to, onboarding programs to participate in, and
full-time jobs to apply for:

- https://github.com/CMSGov
- https://digitalcorps.gsa.gov
- https://codingitforward.com
- https://usds.gov

DSAC (the digital service at CMS) is helping to lead SMEQA (Subject Matter
Expert Qualification Assessments) hiring actions to place industry experts with
Product, Data Science, Engineering, and Design experience into various OpDivs
(Operational Divisions) within the agency.

If we're going to address some of the biggest and most complex problems facing
healthcare, we're going to need all the help we can get.
