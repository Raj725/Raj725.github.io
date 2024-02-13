---
title: Most Useful Neo4j String Functions
author: Raj
type: post
date: 2022-07-02T16:52:29+00:00
draft: true
excerpt: In this post, we will see some of the most used Neo4j String functions, like converting string to numbers(integer/float), date, and list
url: /neo4j/most-useful-neo4j-string-functions/
featuredImage: /wp-content/uploads/2022/07/Screenshot-2022-07-02-at-9.19.33-PM.png
rank_math_internal_links_processed:
  - 1
rank_math_seo_score:
  - 78
rank_math_focus_keyword:
  - Neo4j String
rank_math_primary_category:
  - 2
rank_math_analytic_object_id:
  - 8
categories:
  - Neo4j
tags:
  - Neo4j

---
While working with the data and databases oftentimes we have to deal with the Strings.  In this post, I will try to cover some of the most used Neo4j String functions.<div class="wp-block-uagb-table-of-contents uagb-toc\_\_align-left uagb-toc\_\_columns-1 uagb-block-0f86513c " data-scroll= "1" data-offset= "30" style="" > 

<div class="uagb-toc__wrap">
  <div class="uagb-toc__title">
    Table Of Contents
  </div>
  
  <div class="uagb-toc__list-wrap">
    <ol class="uagb-toc__list">
      <li class="uagb-toc__list">
        <a href="#1-convert-neo4j-string-to-number" class="uagb-toc-link__trigger">1. Convert neo4j string to number</a><ul class="uagb-toc__list">
          <li class="uagb-toc__list">
            <a href="#string-to-integer" class="uagb-toc-link__trigger">String to Integer</a><li class="uagb-toc__list">
              <li class="uagb-toc__list">
                <a href="#running-the-update-query-in-batches" class="uagb-toc-link__trigger">Running the update query in batches</a><li class="uagb-toc__list">
                  <li class="uagb-toc__list">
                    <a href="#string-to-float" class="uagb-toc-link__trigger">String to Float</a>
                  </li></ul>
                </li>
                <li class="uagb-toc__list">
                  <a href="#2-convert-neo4j-string-to-date" class="uagb-toc-link__trigger">2. Convert neo4j string to date</a><ul class="uagb-toc__list">
                    <li class="uagb-toc__list">
                      <a href="#what-if-your-date-is-not-in-the-yyyy-mm-dd-format" class="uagb-toc-link__trigger">What if your date is not in the yyyy-MM-dd format?</a>
                    </li>
                  </ul>
                </li></ul>
              </li>
              
              <li class="uagb-toc__list">
                <a href="#3-convert-the-neo4j-string-to-a-list" class="uagb-toc-link__trigger">3. Convert the neo4j string to a list</a><li class="uagb-toc__list">
                  <a href="#4-convert-other-data-types-to-neo4j-string" class="uagb-toc-link__trigger">4. Convert other data types to neo4j string</a><li class="uagb-toc__list">
                    <a href="#conclusion" class="uagb-toc-link__trigger">Conclusion</a></ul></ul></ol> </div> </div> </div> <h2 class="wp-block-heading">
                      1. Convert neo4j string to number
                    </h2>
                    
                    <p>
                      This happens with everyone. We load the data into the database and then realize that we didn&#8217;t mention the data type for the Integer or Float properties/fields.
                    </p>
                    
                    <p>
                      Most of the time we delete the database, fix the data type in the data load queries, and re-upload the whole data. This method works well for small datasets, but what if you have an extensive dataset, it takes a lot of time to load the data, or it&#8217;s a Production database and you can&#8217;t delete it. Unlike other schema-based databases, we can convert the Neo4j property types on the fly.
                    </p>
                    
                    <p>
                      We will consider a <strong>Product</strong> node type for example. Let&#8217;s assume there are only 3 properties: name, price, and quantity. The name is a String field, Price is a Float field and quantity is a number field, by mistake, we upload all the properties as strings.
                    </p>
                    
                    <p>
                      Let&#8217;s create a product node with all the properties as String, and see how to convert price and quantity to numbers.
                    </p>
                    
                    <div class="wp-block-codemirror-blocks-code-block code-block">
                      <pre class="CodeMirror" data-setting="{&quot;mode&quot;:&quot;gfm&quot;,&quot;mime&quot;:&quot;text/x-gfm&quot;,&quot;theme&quot;:&quot;idea&quot;,&quot;lineNumbers&quot;:true,&quot;styleActiveLine&quot;:true,&quot;lineWrapping&quot;:true,&quot;readOnly&quot;:true,&quot;disableCopy&quot;:true,&quot;language&quot;:&quot;GitHub Flavored Markdown&quot;,&quot;modeName&quot;:&quot;git&quot;}">CREATE (p:Product{name: "Notebook", price: "49.99", quantity: "4"})</pre>
                    </div>
                    
                    <h3 class="wp-block-heading">
                      String to Integer
                    </h3>
                    
                    <p>
                      You can now use the <strong>toInteger</strong> function to convert the <strong>quantity</strong> property from String to Integer.
                    </p>
                    
                    <div class="wp-block-codemirror-blocks-code-block code-block">
                      <pre class="CodeMirror" data-setting="{&quot;mode&quot;:&quot;gfm&quot;,&quot;mime&quot;:&quot;text/x-gfm&quot;,&quot;theme&quot;:&quot;idea&quot;,&quot;lineNumbers&quot;:true,&quot;styleActiveLine&quot;:true,&quot;lineWrapping&quot;:true,&quot;readOnly&quot;:false,&quot;language&quot;:&quot;GitHub Flavored Markdown&quot;,&quot;modeName&quot;:&quot;git&quot;}">MATCH (p:Product)
SET p.quantity = toInteger(p.quantity);</pre>
                    </div>
                    
                    <p>
                      Execute the above Cypher query in the Neo4j and observe the output, it will show the number of properties set and the time it took to execute the query.
                    </p><figure class="wp-block-image size-full is-resized">
                    
                    <img loading="lazy" decoding="async" src="/wp-content/uploads/2022/07/Screenshot-2022-07-02-at-8.31.29-PM.png" alt="" class="wp-image-289" width="731" height="291" srcset="/wp-content/uploads/2022/07/Screenshot-2022-07-02-at-8.31.29-PM.png 974w, /wp-content/uploads/2022/07/Screenshot-2022-07-02-at-8.31.29-PM-300x120.png 300w, /wp-content/uploads/2022/07/Screenshot-2022-07-02-at-8.31.29-PM-768x306.png 768w" sizes="(max-width: 731px) 100vw, 731px" /><figcaption>String to Integer in Neo4j</figcaption></figure> <h3 class="wp-block-heading">
                      Running the update query in batches
                    </h3>
                    
                    <p>
                      The above query updates all the nodes in a single transaction. You may get a low heap memory error if your database is huge. You can convert the above query into auto-committing transactions of smaller sizes. Following query run in transactions of 10000 rows.
                    </p>
                    
                    <div class="wp-block-codemirror-blocks-code-block code-block">
                      <pre class="CodeMirror" data-setting="{&quot;mode&quot;:&quot;gfm&quot;,&quot;mime&quot;:&quot;text/x-gfm&quot;,&quot;theme&quot;:&quot;idea&quot;,&quot;lineNumbers&quot;:true,&quot;styleActiveLine&quot;:true,&quot;lineWrapping&quot;:true,&quot;readOnly&quot;:false,&quot;language&quot;:&quot;GitHub Flavored Markdown&quot;,&quot;modeName&quot;:&quot;git&quot;}">:auto MATCH (p:Product)
CALL {
    WITH p
    SET p.quantity = toInteger(p.quantity)
} IN TRANSACTIONS OF 10000 ROWS;</pre>
                    </div>
                    
                    <h3 class="wp-block-heading">
                      String to Float
                    </h3>
                    
                    <p>
                      You can now use the <strong>toFloat</strong> function to convert the <strong>price</strong> property from String to Float.
                    </p>
                    
                    <div class="wp-block-codemirror-blocks-code-block code-block">
                      <pre class="CodeMirror" data-setting="{&quot;mode&quot;:&quot;gfm&quot;,&quot;mime&quot;:&quot;text/x-gfm&quot;,&quot;theme&quot;:&quot;idea&quot;,&quot;lineNumbers&quot;:true,&quot;styleActiveLine&quot;:true,&quot;lineWrapping&quot;:true,&quot;readOnly&quot;:false,&quot;language&quot;:&quot;GitHub Flavored Markdown&quot;,&quot;modeName&quot;:&quot;git&quot;}">MATCH (p:Product)
SET p.price = toFloat(p.price);</pre>
                    </div>
                    
                    <h2 class="wp-block-heading">
                      2. Convert neo4j string to date
                    </h2>
                    
                    <p>
                      There&#8217;s limited support in Cypher for converting string to date. Cypher only supports yyyy-MM-dd format strings e.g. 2022-06-30. You can use the date() function to convert dates in <strong>yyyy-MM-dd</strong> format to the date type.
                    </p>
                    
                    <div class="wp-block-codemirror-blocks-code-block code-block">
                      <pre class="CodeMirror" data-setting="{&quot;mode&quot;:&quot;gfm&quot;,&quot;mime&quot;:&quot;text/x-gfm&quot;,&quot;theme&quot;:&quot;idea&quot;,&quot;lineNumbers&quot;:true,&quot;styleActiveLine&quot;:true,&quot;lineWrapping&quot;:true,&quot;readOnly&quot;:false,&quot;language&quot;:&quot;GitHub Flavored Markdown&quot;,&quot;modeName&quot;:&quot;git&quot;}">MATCH (e:Event)
SET e.date = date(e.date);</pre>
                    </div>
                    
                    <h4 class="wp-block-heading">
                      <strong>What if your date is not in the yyyy-MM-dd format?</strong>
                    </h4>
                    
                    <p>
                      Let&#8217;s assume your date is in dd-MM-yyyy format e.g. 30-06-2022. You can split the string into a day, month, and year components and use <strong>date()</strong> function to create a date as shown in the following Cypher snippet.
                    </p>
                    
                    <div class="wp-block-codemirror-blocks-code-block code-block">
                      <pre class="CodeMirror" data-setting="{&quot;mode&quot;:&quot;gfm&quot;,&quot;mime&quot;:&quot;text/x-gfm&quot;,&quot;theme&quot;:&quot;idea&quot;,&quot;lineNumbers&quot;:true,&quot;styleActiveLine&quot;:true,&quot;lineWrapping&quot;:true,&quot;readOnly&quot;:false,&quot;language&quot;:&quot;GitHub Flavored Markdown&quot;,&quot;modeName&quot;:&quot;git&quot;}">MATCH (e:Event)
WITH e, [date_component in split(e.date, "-") | toInteger(date_component)] AS date_components
SET e.date = date({day: date_components[0], month: date_components[1], year: date_components[2]})</pre>
                    </div>
                    
                    <p>
                      Alternatively, you can use the simpler function from the APOC library&nbsp;apoc.date.parse. This function allows parsing almost all the formats of dates such as&nbsp;a long date format &#8220;30 June 2022&#8221;.
                    </p>
                    
                    <div class="wp-block-codemirror-blocks-code-block code-block">
                      <pre class="CodeMirror" data-setting="{&quot;mode&quot;:&quot;gfm&quot;,&quot;mime&quot;:&quot;text/x-gfm&quot;,&quot;theme&quot;:&quot;idea&quot;,&quot;lineNumbers&quot;:true,&quot;styleActiveLine&quot;:true,&quot;lineWrapping&quot;:true,&quot;readOnly&quot;:false,&quot;language&quot;:&quot;GitHub Flavored Markdown&quot;,&quot;modeName&quot;:&quot;git&quot;}">MATCH (e:Event)
WITH e, apoc.date.parse(e.date, "ms", "dd MMMMM yyyy") AS ms
SET e.date = date(datetime({epochmillis: ms}))</pre>
                    </div>
                    
                    <h2 class="wp-block-heading">
                      3. Convert the neo4j string to a list
                    </h2>
                    
                    <p>
                      Let&#8217;s assume you have a Car node in the database and you created the <strong>&#8220;colors&#8221;</strong> property as a string but it needs to be a list. You can contact the existing colors property and an <strong>empty list ([])</strong> to convert it to a list.
                    </p>
                    
                    <div class="wp-block-codemirror-blocks-code-block code-block">
                      <pre class="CodeMirror" data-setting="{&quot;mode&quot;:&quot;gfm&quot;,&quot;mime&quot;:&quot;text/x-gfm&quot;,&quot;theme&quot;:&quot;idea&quot;,&quot;lineNumbers&quot;:true,&quot;styleActiveLine&quot;:true,&quot;lineWrapping&quot;:true,&quot;readOnly&quot;:false,&quot;language&quot;:&quot;GitHub Flavored Markdown&quot;,&quot;modeName&quot;:&quot;git&quot;}">MATCH (c:Car)
SET c.colors = c.colors + [];</pre>
                    </div>
                    
                    <p>
                      If you have delimiter-separated values you can use the split() function to convert them to a list.
                    </p>
                    
                    <div class="wp-block-codemirror-blocks-code-block code-block">
                      <pre class="CodeMirror" data-setting="{&quot;mode&quot;:&quot;gfm&quot;,&quot;mime&quot;:&quot;text/x-gfm&quot;,&quot;theme&quot;:&quot;idea&quot;,&quot;lineNumbers&quot;:true,&quot;styleActiveLine&quot;:true,&quot;lineWrapping&quot;:true,&quot;readOnly&quot;:false,&quot;language&quot;:&quot;GitHub Flavored Markdown&quot;,&quot;modeName&quot;:&quot;git&quot;}">RETURN split("black,white", ",") as colors</pre>
                    </div>
                    
                    <h2 class="wp-block-heading">
                      4. Convert other data types to neo4j string
                    </h2>
                    
                    <p>
                      You can use the <strong>toString()</strong> function to convert any other data type to String. This can be used for any data type like an integer, float, boolean, string, point, duration, date, time, localtime, localdatetime, or datetime value to a string.
                    </p>
                    
                    <h2 class="wp-block-heading">
                      Conclusion
                    </h2>
                    
                    <p>
                      I hope this tutorial helped you in working with Neo4j strings. Please comment if you face any issues or need any help with anything related to Neo4j.
                    </p>
                    
                    <p>
                      Please refer to <a href="https://neo4j.com/docs/cypher-manual/current/functions/string">Neo4j documentation</a> for more String functions.
                    </p>