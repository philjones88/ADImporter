# ADImporter
Credit to Helge Klein - https://helgeklein.com/blog/2015/02/creating-realistic-test-user-accounts-active-directory/

When you need to simulate a real Active Directory with thousands of users you quickly find that creating realistic test accounts is not trivial. Sure enough, you can whip up a quick PowerShell one-liner that creates any number of accounts, but what if you need real first and last names? Real (existing) addresses? Postal codes matching phone area codes? I could go on. The point is that you need two things: input files with names, addresses etc. And script logic that creates user accounts from that data. This blog post provides both.

# Mission Statement

The purpose of the script is to create an arbitrary number of user accounts with the following properties:

* Logon name (sAMAccountName)
* User principal name (UPN)
* First name
* Last name 
* Display name
* E-mail address
* Street
* City
* Postal code
* State
* Country
* Phone number
* Company
* Department
* Title


Active directory user accounts created by the PowerShell script

# Realism

In order to create realistic results we need data, lists: firstnames, surnames, addresses and a mapping between postal and phone area codes. The script CreateDemoUsers.ps1 expects separate CSV files for each of these. I have included some files with assorted information for UK addresses, and assorted nationality names.

If you want your users to “live” in another country you need to provide the lists yourself.

# Using CreateDemoUsers.ps1

Running the script is simple enough: just start it, there are no commandline parameters. I have run it directly on my lab’s domain controller but it should work from a domain member, too.

Before you execute the script you might want to configure a few things, though. Take a look at the global variables section at the head of the script.
There you can configure important things like how many users to create, which OU to create them in, how many different addresses to use and many other things. That section also contains the names of the data files the script requires. If you use my files you do not need to change anything, but if you create your own files you might want to make sure the file names match.
