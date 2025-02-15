# 2 Description

The Consent Management Building Block enables services for individuals to
approve the use of their personal data by defining the principles, functions and
architecture of an information system. For organisations that process personal
data​,​ it provides the ability to know the ​individual's will and legitimately
process such personal data.

The Consent Management Building Block is a process-oriented GovStack Building
Block facilitating auditable bilateral agreements within a multi-agent
environment that integrates with most other BBs.

This specification has used several available and recognised open standards
below and legal frameworks (such as the [GDPR](https://gdpr.eu/)) for laying the
groundwork for its approach to consent management. :

- [Kantara Initiative](https://kantarainitiative.org/download/7902/) - Consent
  Specification
- [ISO 29184: 2020](https://www.iso.org/standard/70331.html): Online Privacy
  Notices and Consent
- [ISO/IEC 29100:2011](https://www.iso.org/standard/45123.html): Privacy
  framework
- [ISO/TS 17975:2015](https://www.iso.org/standard/61186.html) Health
  informatics — Principles and data requirements for consent in the Collection,
  Use or Disclosure of personal health information
- [ISO/IEC TS 27560](https://www.iso.org/standard/80392.html) — Consent record
  information structure (under development)

## 2.1 What Consent Is

In the GovStack context, consent is understood as a voluntary declaration by an
individual to approve the processing of their Personal data. It is one specific
justification for personal data processing that is assumed to be required by
legal or ethical conditions. It assumes that the person can decide on processing
their personal data, managed in and by other GovStack BBs, and also that the
person is free to withdraw their consent at any time.

## 2.2 What Consent Is Not

The use of _consent_ should be avoided in cases as below, which are not part of
this specification:

- When a person is simply informed of the processing of the data by the
  organisation as part of the service provided under contract or by an
  authority.
- When consent does not have to be obtained in a situation where the entity does
  not identify or cannot identify people with reasonable effort.

## 2.3 Consent Agreement Lifecycle

The life cycle of consent management starts and ends within the organisation
responsible for the information system. The organisation knows the context in
which the information system operates and the intended purpose of the service.
The rules and regulations to be applied for a given level of assurance define
the functional framework for consent management.

Consent management deals with transparency on data usage in a given context.
Thus privacy-by-design of the system's actors is often an excellent guiding
principle for interpreting international, national and organisational policies
and governance principles to implement the functional consent framework. A
tangible outcome from a data protection impact analysis (DPIA) is a structured
approach that can deliver the input for the actual implementation of the Consent
BB.

Individual consent is captured within the context of digital interaction. This
interaction is composite of all the information systems involved, not solely
Consent BB. Thus, the legal and ethical boundaries of consent are defined in the
entirety of the interaction. In particular, consent, as defined by ISO/TS
17975:2015(E), should be seen as a "set of agreements and constraints" that an
informed and knowledgeable [individual] agrees to apply to their data
processing. This definition, not based on the purpose of the data usage, can
lead to a consent management framework also incorporating authorisations or
unrelated constraints of the system. For example, in health information and
healthcare service delivery, consent is also the process whereby a set of
constraints is agreed upon so that information may be collected and used or
disclosed. However, it is also the outcome of the process. As a rule of thumb,
limiting unintended secondary usage of data is helpful to separate "consent" for
a purpose from "consent" as an agreement to constraints and authorisation
imposed by the system's functional requirements.

As a result, the organisation responsible for the information system is the
driver of the definition of the functional consent management framework. It is
also the function of the organisation to design the workflow for obtaining and
processing the consent in a way that is purposeful, but not annoying for
individuals or data processors with unnecessary bureaucratic overhead. From this
framework, the Consent Building Block achieves its purpose by employing Consent
Agreements that contain the following:

- A data policy that could be reused across multiple consent agreements (for
  example, based on GDPR or any specific regulation)
- The purpose of consent, processed data attributes
- Signatures

A consent agreement life-cycle has four main phases[^2], as illustrated in the
figure below: ![alt_text](images/consent-lifecycle.png 'image_tooltip')
[Diagram Source](https://app.moqups.com/P01asyy7ba/view/page/a2cb2359e)

**Definition**: In this phase, the organisation (a Data Provider or a Data
Consumer) adopts and defines a Data Policy that applies to the industry or
sector-specific data usage as a template. While this phase is considered a
“black box” to the Consent BB, it is an essential reference point for
configuration and compatibility checks in all following phases.

**Preparation**: In this phase, the organisation (A Data Provider or a Data
Consumer) that intends to process personal data configures the Consent Agreement
and relevant rules for its use. An organisation could use personal data for
third-party data sharing, as an example.

**Capture**: In this phase, the Individual can review the Consent Agreement and,
once agreed, it is captured in a Consent Record by the organisation and stored
for verification. This allows an auditor to check and ensure records are in
place to process the individual's personal data. In future, this phase could
also encompass delegation and other individual use cases.

**Proof**: In this phase, an organisation (A Data Provider or a Data Consumer)
can demonstrate that a valid record exists for performing data processing within
itself or with other organisations. This allows for internal usage and for an
auditor to verify and ensure records are in place to process the individual's
personal data.

## 2.4 Actors

The following actors (performing a distinct human role) are identified to be
acting on the Consent BB.
![alt_text](images/consent-bb-actors-01.png 'image_tooltip')
![alt_text](images/consent-bb-actors-02.png 'Indidivual and DPAs')

[Diagram Source](https://app.moqups.com/P01asyy7ba/view/page/ad64222d5)

### 2.4.1 Individual

The capabilities for individuals that Consent BB supports are:

- viewing and understanding Data Policies applying to their personal data
  processing;
- agreeing and disagreeing with and toggling between the conditions of personal
  data use as described in the Consent Agreement;
- obtaining copies of their Consent Agreement(s);
- delegating their consent rights (_out-of-scope for current technical release_)

The scope for version 1.0 of Consent BB assumes that the Individual is acting
for her-/himself. Ultimately the Consent BB will include in the Consenting
Process the capacity to sign a Consent Agreement in the name of another
individual - to act as the Delegate, which is used as the criterion for
technical implementation. However, the Delegate and the Individual relationship
is expected to be maintained outside of the Consent Manager, which assumes that
the person signing the Consent Agreement (i.e. Consenter) has been authorised to
do so.

### 2.4.2 Administrator

The Administrator (Data Provider or Data Consumer Admin) configures the consent
management system on behalf of the organisation. The main actions expected to
perform via Consent BB are:

- configuring Data Policies, requesting and signing Consent Agreements with
  Individuals;
- viewing (reading, exporting) the Consent Agreements and relevant reports;
- event-driven (opt-in or opt-out) subscription to (notifications of) changes in
  Consent Agreements;
- logging and maintaining an auditable overview of all personal data
  transactions according to Consent Agreements as well as configuration
  versions.

### 2.4.3 Data Processing Auditor

The main actions a Data Processing Auditor (or Data Protection Officer, DPO) is
expected to perform via Consent BB are:

1. auditing tracking the consents (opt-in/opt-out);
2. auditing tracking Data Policy changes and configuration conformance with it;
3. viewing (reading, exporting) the Consent Agreements and relevant reports in a
   verifiable form.

The Data Processing Auditor relies on an audit universe defined by the control
and risk management of the specific project and context (i.e. outside the
Consent BB). “_Who needs to consent to what_” is the outcome of a DPIA (Data
Protection Impact Analysis), ensuring that the data policies are compliant with
the relevant data protection regulations for the project.

For the implementation of a specific use case, it is important to distinguish
the Data Processing Auditor, an actor described here, from a data policy
auditor, an actor of the risk organisation. It is expected that the two roles
are coordinated in the risk management process. Within the Consent BB, the Data
Processing Auditor performs the tasks that will allow a data policy auditor to
confirm that the implemented system complies with existing regulations demanding
consent.
