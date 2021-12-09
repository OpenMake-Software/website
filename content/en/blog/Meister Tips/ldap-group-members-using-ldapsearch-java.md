---
title: "LDAP Group Members using ldapsearch and Java"
date: "2017-04-13"
categories: 
  - "meister-continuous-build"
tags: 
  - "ldapsearch"
coverImage: "Image-for-Collaborative.jpg"
---

## Using ldapsearch with LDAP Group Members.

Ldapsearch has become a handy tool for us. Here is how we use it. Many of our customers are striving to protect a single sign-on, so LDAP becomes critical to achieving their goals. We've done quite a bit of work around LDAP coding. The use of ldapsearch has become a popular part of our coding. I thought it would be helpful to expose has we have used it for our applications.![](images/Image-for-Collaborative-300x212.jpg)

<div>
<img src="/images/Image-for-Collaborative-300x212.jpg" alt="LDAP" />
</div>
<br>

We use the LDAP server provided by <a href="http://www.forumsys.com/tutorials/integration-how-to/ldap/online-ldap-test-server/">Forum Systems Online LDAP Test Server</a>.

Here is the ldapsearch command line:

```bash
ldapsearch -W -h ldap.forumsys.com -D "cn=read-only-admin,dc=example,dc=com" -b "dc=example,dc=com" "ou=mathematicians"

```

\-W : Prompt for password

\-h : ldap server to use

\-D : is the binddn (userid to login to the ldap server with)

\-b : is the base search root and the last parameter is the search filter

Results from the ldapsearch:

```bash
Enter LDAP Password: 
# extended LDIF
#
# LDAPv3
# base <dc=example,dc=com> with scope subtree
# filter: ou=mathematicians
# requesting: ALL
#

# mathematicians, example.com
dn: ou=mathematicians,dc=example,dc=com
uniqueMember: uid=euclid,dc=example,dc=com
uniqueMember: uid=riemann,dc=example,dc=com
uniqueMember: uid=euler,dc=example,dc=com
uniqueMember: uid=gauss,dc=example,dc=com
uniqueMember: uid=test,dc=example,dc=com
ou: mathematicians
cn: Mathematicians
objectClass: groupOfUniqueNames
objectClass: top

# search result
search: 2
result: 0 Success

# numResponses: 2
# numEntries: 1
```

Here is the same ldap query using Java:

```java
import java.util.ArrayList;
import java.util.Hashtable;
import java.util.Vector;

import javax.naming.Context;
import javax.naming.NameNotFoundException;
import javax.naming.NamingEnumeration;
import javax.naming.NamingException;
import javax.naming.directory.Attribute;
import javax.naming.directory.Attributes;
import javax.naming.directory.SearchControls;
import javax.naming.directory.SearchResult;
import javax.naming.ldap.InitialLdapContext;
import javax.naming.ldap.LdapContext;

public class memberof
{
 public static void main(String\[\] args)
 {
  ArrayList members = new ArrayList();

  String ldapUsername = "cn=read-only-admin,dc=example,dc=com";
  String ldapPassword = "password";
  String servername = "ldap://ldap.forumsys.com:389";
  String searchbase = "dc=example,dc=com";
  String searchfilter = "ou=mathematicians";

  Hashtable<String, Object> env = new Hashtable<String, Object>();
  env.put(Context.SECURITY\_AUTHENTICATION, "simple");
  env.put(Context.SECURITY\_PRINCIPAL, ldapUsername);
  env.put(Context.SECURITY\_CREDENTIALS, ldapPassword);
  env.put(Context.INITIAL\_CONTEXT\_FACTORY, "com.sun.jndi.ldap.LdapCtxFactory");
  env.put(Context.PROVIDER\_URL, servername);

  // the following is helpful in debugging errors
  // env.put("com.sun.jndi.ldap.trace.ber", System.err);

  LdapContext ctx;
  try
  {
   ctx = new InitialLdapContext(env, null);

   NamingEnumeration results = null;
   try
   {
    SearchControls controls = new SearchControls();
    controls.setSearchScope(SearchControls.SUBTREE\_SCOPE);
    results = ctx.search(searchbase, searchfilter, controls);

    while (results.hasMore())
    {
     SearchResult searchResult = (SearchResult) results.next();
     Attributes attributes = searchResult.getAttributes();
     Attribute attr = attributes.get("uniqueMember");
     
     for (int i=0;i<attr.size();i++)
     {
      members.add((String) attr.get(i));
     }
    }
   }
   catch (NameNotFoundException e)
   {
    // The base context was not found.
    // Just clean up and exit.
   }
   catch (NamingException e)
   {
    throw new RuntimeException(e);
   }
   finally
   {
    if (results != null)
    {
     try
     {
      results.close();
     }
     catch (Exception e)
     {
      // Never mind this.
     }
    }
    if (ctx != null)
    {
     try
     {
      ctx.close();
     }
     catch (Exception e)
     {
      // Never mind this.
     }
    }
   }

   // Loop through the memebers of the and print them out
   for (int i = 0; i < members.size(); i++)
   {
    System.out.println(members.get(i));
   }
  }
  catch (NamingException e1)
  {
   // TODO Auto-generated catch block
   e1.printStackTrace();
  }
 }
}
```

Results from the Java program:

```bash
uid=euclid,dc=example,dc=com
uid=riemann,dc=example,dc=com
uid=euler,dc=example,dc=com
uid=gauss,dc=example,dc=com
uid=test,dc=example,dc=com
```
