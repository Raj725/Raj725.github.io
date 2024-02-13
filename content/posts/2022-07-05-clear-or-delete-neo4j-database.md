---
title: How To Clear Or Delete Neo4j Database?
author: Raj
type: post
draft: true
date: 2022-07-05T14:02:35+00:00
excerpt: |
  You will learn about the best ways to 
  clear or delete Neo4j database as per specific needs. Neo4j DELETE and  REMOVE Cluases.
url: /neo4j/clear-or-delete-neo4j-database/
featuredImage: /wp-content/uploads/2022/07/Screenshot-2022-07-05-at-7.12.42-PM.png
rank_math_seo_score:
  - 81
rank_math_focus_keyword:
  - neo4j
rank_math_internal_links_processed:
  - 1
rank_math_primary_category:
  - 2
rank_math_analytic_object_id:
  - 9
categories:
  - Neo4j
tags:
  - Cypher
  - Neo4j

---
I am sharing the best ways to clear or delete the Neo4j database as per your specific needs. <div class="wp-block-uagb-table-of-contents uagb-toc\_\_align-left uagb-toc\_\_columns-1 uagb-block-3f75a281 " data-scroll= "1" data-offset= "30" style="" > 

<div class="uagb-toc__wrap">
  <div class="uagb-toc__title">
    Table Of Contents <svg xmlns="https://www.w3.org/2000/svg" viewBox= "0 0 384 512"><path d="M192 384c-8.188 0-16.38-3.125-22.62-9.375l-160-160c-12.5-12.5-12.5-32.75 0-45.25s32.75-12.5 45.25 0L192 306.8l137.4-137.4c12.5-12.5 32.75-12.5 45.25 0s12.5 32.75 0 45.25l-160 160C208.4 380.9 200.2 384 192 384z"></path></svg>
  </div>
  
  <div class="uagb-toc__list-wrap">
    <ol class="uagb-toc__list">
      <li class="uagb-toc__list">
        <a href="#neo4j-remove-clause" class="uagb-toc-link__trigger">Neo4j Remove Clause</a><ul class="uagb-toc__list">
          <li class="uagb-toc__list">
            <a href="#remove-node-properties" class="uagb-toc-link__trigger">Remove Node properties</a><li class="uagb-toc__list">
              <li class="uagb-toc__list">
                <a href="#remove-relationship-properties" class="uagb-toc-link__trigger">Remove Relationship properties</a><li class="uagb-toc__list">
                  <li class="uagb-toc__list">
                    <a href="#remove-a-label-from-a-node" class="uagb-toc-link__trigger">Remove a label from a node</a>
                  </li></ul>
                </li>
                <li class="uagb-toc__list">
                  <a href="#neo4j-delete-clause" class="uagb-toc-link__trigger">Neo4j Delete Clause</a><ul class="uagb-toc__list">
                    <li class="uagb-toc__list">
                      <a href="#delete-relationships" class="uagb-toc-link__trigger">Delete Relationships</a><li class="uagb-toc__list">
                        <li class="uagb-toc__list">
                          <a href="#delete-nodes" class="uagb-toc-link__trigger">Delete Nodes</a>
                        </li></ul>
                      </li></ul>
                      <li class="uagb-toc__list">
                        <a href="#completely-clear-or-delete-neo4j-data" class="uagb-toc-link__trigger">Completely Clear or Delete Neo4j data</a></ol> </div> </div> </div> <h2 class="wp-block-heading">
                          Neo4j Remove Clause
                        </h2>
                        
                        <p>
                          The <strong>REMOVE</strong> clause is used to remove properties from nodes or relationships. It is also used to remove labels from the nodes.
                        </p>
                        
                        <h4 class="wp-block-heading">
                          Remove Node properties
                        </h4>
                        
                        <p>
                          There are 2 ways to remove the property from a node. You can either use a REMOVE clause or a SET clause. Using SET, You can set the property value as null and it will remove the property because Neo4j doesn&#8217;t allow storing null properties. Storing null is equivalent to removing it.
                        </p><figure class="wp-block-image size-large is-resized">
                        
                        <img loading="lazy" decoding="async" src="/wp-content/uploads/2022/07/Screenshot-2022-07-05-at-6.19.35-PM-1024x740.png" alt="" class="wp-image-323" width="560" height="404" srcset="/wp-content/uploads/2022/07/Screenshot-2022-07-05-at-6.19.35-PM-1024x740.png 1024w, /wp-content/uploads/2022/07/Screenshot-2022-07-05-at-6.19.35-PM-300x217.png 300w, /wp-content/uploads/2022/07/Screenshot-2022-07-05-at-6.19.35-PM-768x555.png 768w, /wp-content/uploads/2022/07/Screenshot-2022-07-05-at-6.19.35-PM.png 1472w" sizes="(max-width: 560px) 100vw, 560px" /><figcaption>Screenshot: Remove Node Properties</figcaption></figure> <p>
                          <strong>1. Remove node property using REMOVE Clause</strong>
                        </p>
                        
                        <div class="wp-block-codemirror-blocks-code-block code-block">
                          <pre class="CodeMirror" data-setting="{&quot;mode&quot;:&quot;sql&quot;,&quot;mime&quot;:&quot;text/x-mysql&quot;,&quot;theme&quot;:&quot;neat&quot;,&quot;lineNumbers&quot;:true,&quot;styleActiveLine&quot;:true,&quot;lineWrapping&quot;:true,&quot;readOnly&quot;:true,&quot;language&quot;:&quot;MySQL&quot;,&quot;modeName&quot;:&quot;mysql&quot;}">MATCH (p:Product)
REMOVE p.discount;</pre>
                        </div>
                        
                        <p>
                          <strong>2. Remove node property using SET clause</strong>
                        </p>
                        
                        <div class="wp-block-codemirror-blocks-code-block code-block">
                          <pre class="CodeMirror" data-setting="{&quot;mode&quot;:&quot;sql&quot;,&quot;mime&quot;:&quot;text/x-mysql&quot;,&quot;theme&quot;:&quot;neat&quot;,&quot;lineNumbers&quot;:true,&quot;styleActiveLine&quot;:true,&quot;lineWrapping&quot;:true,&quot;readOnly&quot;:true,&quot;language&quot;:&quot;MySQL&quot;,&quot;modeName&quot;:&quot;mysql&quot;}">MATCH (p:Product)
SET p.name=null;</pre>
                        </div>
                        
                        <p>
                          3.<strong> Remove all node properties. </strong>REMOVE clause can not be used to remove all the properties. Instead, SET can be used to set node = empty map, which will remove all the properties from node.
                        </p>
                        
                        <div class="wp-block-codemirror-blocks-code-block code-block">
                          <pre class="CodeMirror" data-setting="{&quot;mode&quot;:&quot;sql&quot;,&quot;mime&quot;:&quot;text/x-mysql&quot;,&quot;theme&quot;:&quot;neat&quot;,&quot;lineNumbers&quot;:true,&quot;styleActiveLine&quot;:true,&quot;lineWrapping&quot;:true,&quot;readOnly&quot;:true,&quot;language&quot;:&quot;MySQL&quot;,&quot;modeName&quot;:&quot;mysql&quot;}">MATCH (p:Product)
SET p={};</pre>
                        </div>
                        
                        <h4 class="wp-block-heading">
                          Remove Relationship properties
                        </h4>
                        
                        <p>
                          Removing properties from the relationship is identical to removing properties from the nodes. You just need to match the relationship and use the above syntax. For example:
                        </p>
                        
                        <div class="wp-block-codemirror-blocks-code-block code-block">
                          <pre class="CodeMirror" data-setting="{&quot;mode&quot;:&quot;sql&quot;,&quot;mime&quot;:&quot;text/x-mysql&quot;,&quot;theme&quot;:&quot;neat&quot;,&quot;lineNumbers&quot;:true,&quot;styleActiveLine&quot;:true,&quot;lineWrapping&quot;:true,&quot;readOnly&quot;:true,&quot;language&quot;:&quot;MySQL&quot;,&quot;modeName&quot;:&quot;mysql&quot;}">MATCH (n:Product)-[r:HAS_DISCOUNT]-&gt;(d:Discount)
REMOVE r.occasion</pre>
                        </div>
                        
                        <h4 class="wp-block-heading">
                          Remove a label from a node
                        </h4>
                        
                        <div class="wp-block-codemirror-blocks-code-block code-block">
                          <pre class="CodeMirror" data-setting="{&quot;mode&quot;:&quot;sql&quot;,&quot;mime&quot;:&quot;text/x-mysql&quot;,&quot;theme&quot;:&quot;neat&quot;,&quot;lineNumbers&quot;:true,&quot;styleActiveLine&quot;:true,&quot;lineWrapping&quot;:true,&quot;readOnly&quot;:true,&quot;language&quot;:&quot;MySQL&quot;,&quot;modeName&quot;:&quot;mysql&quot;}">MATCH (n:Product)
REMOVE n:Product</pre>
                        </div>
                        
                        <h2 class="wp-block-heading">
                          Neo4j Delete Clause
                        </h2>
                        
                        <p>
                          The <code>&lt;strong>DELETE&lt;/strong></code> is used to delete nodes, relationships, or paths.
                        </p>
                        
                        <h4 class="wp-block-heading">
                          Delete Relationships
                        </h4>
                        
                        <p>
                          We may need this query when you accidentally created incorrect relationships or you decided to change the data model.
                        </p>
                        
                        <div class="wp-block-codemirror-blocks-code-block code-block">
                          <pre class="CodeMirror" data-setting="{&quot;mode&quot;:&quot;sql&quot;,&quot;mime&quot;:&quot;text/x-mysql&quot;,&quot;theme&quot;:&quot;neat&quot;,&quot;lineNumbers&quot;:true,&quot;styleActiveLine&quot;:true,&quot;lineWrapping&quot;:true,&quot;readOnly&quot;:true,&quot;language&quot;:&quot;MySQL&quot;,&quot;modeName&quot;:&quot;mysql&quot;}">MATCH (:Product)-[c:HAS_CATEGORY]-&gt;(:Category)
DELETE c</pre>
                        </div>
                        
                        <h4 class="wp-block-heading">
                          Delete Nodes
                        </h4>
                        
                        <p>
                          Please note that we can not delete a node without deleting the connected relationships. We should either delete all the relationships first or delete them along with the node or use DETACH DELETE on a node that will detach node from connected node and delete it. <strong>OPTIONAL MATCH</strong> clause is used to make sure that nodes without relationships are also deleted, without <strong>OPTIONAL MATCH</strong> nodes having no relationships will not match the pattern and will not be deleted.
                        </p>
                        
                        <div class="wp-block-codemirror-blocks-code-block code-block">
                          <pre class="CodeMirror" data-setting="{&quot;mode&quot;:&quot;sql&quot;,&quot;mime&quot;:&quot;text/x-mysql&quot;,&quot;theme&quot;:&quot;neat&quot;,&quot;lineNumbers&quot;:true,&quot;styleActiveLine&quot;:true,&quot;lineWrapping&quot;:true,&quot;readOnly&quot;:true,&quot;language&quot;:&quot;MySQL&quot;,&quot;modeName&quot;:&quot;mysql&quot;}">MATCH (p:Product)
OPTIONAL MATCH (p)-[r:HAS_CATEGORY]-&gt;(:Category)
DELETE p, r</pre>
                        </div>
                        
                        <p>
                          If there are no relationships to the node you can simply delete the node as follows:
                        </p>
                        
                        <div class="wp-block-codemirror-blocks-code-block code-block">
                          <pre class="CodeMirror" data-setting="{&quot;mode&quot;:&quot;sql&quot;,&quot;mime&quot;:&quot;text/x-mysql&quot;,&quot;theme&quot;:&quot;neat&quot;,&quot;lineNumbers&quot;:true,&quot;styleActiveLine&quot;:true,&quot;lineWrapping&quot;:true,&quot;readOnly&quot;:true,&quot;language&quot;:&quot;MySQL&quot;,&quot;modeName&quot;:&quot;mysql&quot;}">MATCH (p:Product)
DELETE p</pre>
                        </div>
                        
                        <h3 class="wp-block-heading">
                          Completely Clear or Delete Neo4j data
                        </h3>
                        
                        <div class="wp-block-codemirror-blocks-code-block code-block">
                          <pre class="CodeMirror" data-setting="{&quot;mode&quot;:&quot;sql&quot;,&quot;mime&quot;:&quot;text/x-mysql&quot;,&quot;theme&quot;:&quot;neat&quot;,&quot;lineNumbers&quot;:true,&quot;styleActiveLine&quot;:true,&quot;lineWrapping&quot;:true,&quot;readOnly&quot;:true,&quot;language&quot;:&quot;MySQL&quot;,&quot;modeName&quot;:&quot;mysql&quot;}">MATCH (n)
DETACH DELETE n</pre>
                        </div>
                        
                        <p>
                          Above Cypher snippet works fine for small databases but for big databases, you need to delete the data in auto-commiting transactions which deletes data in multiple transactions and prevents the Neo4j throwing out of memory error. The following query does not work for older versions of the Neo4j(< version 4.4). If it doesn&#8217;t work for you, you can use APOC Library to delete the database using the periodic commit procedure.
                        </p>
                        
                        <div class="wp-block-codemirror-blocks-code-block code-block">
                          <pre class="CodeMirror" data-setting="{&quot;mode&quot;:&quot;sql&quot;,&quot;mime&quot;:&quot;text/x-mysql&quot;,&quot;theme&quot;:&quot;neat&quot;,&quot;lineNumbers&quot;:true,&quot;styleActiveLine&quot;:true,&quot;lineWrapping&quot;:true,&quot;readOnly&quot;:true,&quot;language&quot;:&quot;MySQL&quot;,&quot;modeName&quot;:&quot;mysql&quot;}">:auto MATCH (n)
CALL {
    WITH n
    DETACH DELETE n
} IN TRANSACTIONS OF 100000 ROWS</pre>
                        </div><figure class="wp-block-image size-full">
                        
                        <img loading="lazy" decoding="async" width="848" height="414" src="/wp-content/uploads/2022/07/Screenshot-2022-07-05-at-7.30.11-PM.png" alt="" class="wp-image-331" srcset="/wp-content/uploads/2022/07/Screenshot-2022-07-05-at-7.30.11-PM.png 848w, /wp-content/uploads/2022/07/Screenshot-2022-07-05-at-7.30.11-PM-300x146.png 300w, /wp-content/uploads/2022/07/Screenshot-2022-07-05-at-7.30.11-PM-768x375.png 768w" sizes="(max-width: 848px) 100vw, 848px" /><figcaption>Delete Neo4j data with auto committing Transactions</figcaption></figure> <h5 class="wp-block-heading">
                          References:
                        </h5>
                        
                        <ol>
                          <li>
                            Neo4j <a href="https://neo4j.com/docs/cypher-manual/current/clauses/remove/" target="_blank" rel="noreferrer noopener">REMOVE</a> documentation
                          </li>
                          <li>
                            Neo4j <a href="https://neo4j.com/docs/cypher-manual/current/clauses/delete/" target="_blank" rel="noreferrer noopener">DELETE</a> documentation
                          </li>
                        </ol>