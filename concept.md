Issue ticketing system using Github
===================================

Concepts/Scheme
---------------
* Project  
  Git module: `project-<seq>`

    * Project metadata  
      File: `metadata`;  
      Content: JSON object; Project name, dates, creator;

    * Scheme definition  
      File: `scheme`;  
      Content: JSON object; Issue types, fields;

    * Issue  
      Directory: `issue-<seq>`

        * Issue metadata  
          File: `metadata`;  
          Content: JSON object; date created, creator, due date, priority/severity, attachment metadata;

        * Summary  
          File: `summary`;  
          Content: Markdown;  

        * Description  
          File: `description`;  
          Content: Markdown;  

        * Comments  
          Git commit comment: 
          Content: Markdown?;  

        * Attachments  
          File: `attachment-<checksum>`; checksum: SHA2 hash of file contents;  
          Content: Base64; DATA;

Notes
-----
* Files are attached to comments.

* All JSON should be UTF-8 encoded.

Questions
---------
* How do we model form fields?
  JSON object; Array of: field name, field type
  Is there a standard list of field types? plaintext, boolean, integer, float, blob, etc.

* How do we handle ticket assignment?
  Is ticket assignment even a thing? Simply commenting and including their name could trigger an email.
  How do you see which tickets you're currently working on?
  How does Github do it?

* How do we handle search?
  Lucene? (is it better to store things as massive JSON objects? (apart from attachments))
  Is there a Git search thinger?
  Build our own?

* How do we handle due date and priority?
  Included in the issue metadata?

* How can we simply add a comment without changing the issue, metadata, etc.
  Can it be done in Git?  Arbitary modification a designated "scratch file"? "Experts only"?

* How will we alidate files and content?
  Validation against the known types?
