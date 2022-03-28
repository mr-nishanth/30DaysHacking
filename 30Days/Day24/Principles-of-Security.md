#	Day 24

#### 06-02-2022

# TryHackMe Rank  34785 ( 58 Streak )


# Principles of Security

[TryHackMe Principles of Security ](https://tryhackme.com/room/principlesofsecurity)

## CIA

-	The CIA triad is an information security model that is used in consideration throughout creating a security policy. T
-	his model has an extensive background, ranging from being used in *1998*.

-	*Confidentiality, Integrity and Availability (CIA)*

###	Confidentiality

-	This element is the protection of data from unauthorized access and misuse.

-	for example, employee records and accounting documents will be considered sensitive.

-	Confidentiality will be provided in the sense that only HR administrators will access employee records, where vetting and tight access controls are in place.

-	Accounting records are less valuable (and therefore less sensitive), so not as stringent access controls would be in place for these documents.

###	Integrity

-	The CIA triad element of integrity is the condition where information is kept accurate and consistent unless authorized changes are made.

-	Many defences to ensure integrity can be put in place.

-	Access control and rigorous authentication can help prevent authorized users from making unauthorized changes.

-	Hash verifications and digital signatures can help ensure that transactions are authentic and that files have not been modified or corrupted.

-	for example, in a breach of confidentiality


###	Availability

-	Availability is achieved through a combination of many elements, including:

-	Having reliable and well-tested hardware for their information technology servers (i.e. reputable servers)

-	Having redundant technology and services in the case of failure of the primary

-	implementing well-versed security protocols to protect technology and services from attack



Q1.	What element of the CIA triad ensures that data cannot be altered by unauthorised people?

Q2.	What element of the CIA triad ensures that data is available?

Q3.	What element of the CIA triad ensures that data is only accessed by authorised people?

---

## Principles of

-	The levels of access given to individuals are determined on two primary factors:

	-	The individual's role/function within the organisation
    	-	The sensitivity of the information being stored on the system

-	Two key concepts are used:

	-	Privileged Identity Management (PIM) and Privileged Access Management (or PAM for short).


## Security Model

-	Any system or piece of technology storing information is called an information system.

### The Bell-La Padula Model

-	The Bell-La Padula Model is used to achieve confidentiality.

-	This model has a few assumptions, such as an organisation's hierarchical structure it is used in, where everyone's responsibilities/roles are well-defined.


-	The model works by granting access to pieces of data (called objects) on a strictly need to know basis.

-	This model uses the rule *"no write down, no read up"*.

-	The Bell LaPadula Model is popular within organisations such as governmental and military.

-	This is because members of the organisations are presumed to have already gone through a process called vetting.

-	Vetting is a screening process where applicant's backgrounds are examined to establish the risk they pose to the organisation.

-	Therefore, applicants who are successfully vetted are assumed to be trustworthy - which is where this model fits in.
