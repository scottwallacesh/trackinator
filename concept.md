Issue ticketing system using Github
===================================

Concepts/Scheme
---------------
* Project  
  Git module: `project-<id>`; id: SHA2 hash of name, date created and creator username;

    * Project metadata  
      File: `metadata`;  
	  Content: JSON object; Name, Dates, Creator;

    * Scheme definition  
	  File: `scheme`;  
      Content: JSON object; Issue types, fields;

        * Issue  
          Directory: `issue-<id>`; id: SHA2 hash of name, date created and creator username;  

	    * Issue metadata  
  		  File: `metadata`;  
          Content: JSON object; Name, Dates, Creator;  

	    * Summary  
		  File: `summary`;  
		  Content: Markdown;  

	    * Description  
	  	  File: `description`;  
		  Content: Markdown;  

	    * Comment  
		  File: `comment-<id>`; id: SHA2 hash of comment, date created and creator username;  
		  Content: Markdown;  

		    * Comment Metadata  
		      Commit comment;  
		      Content: JSON object; Date, comment creator, reason for edit (if edited);

		    * Attachments  
	          File: `attachment-<id>`; id: SHA2 hash of file contents;  
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
