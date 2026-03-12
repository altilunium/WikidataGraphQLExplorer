# wdquery

[GraphQL-powered](https://www.wikidata.org/wiki/Wikidata:Wikibase_GraphQL) Wikidata item advanced search.

<img width="1348" height="694" alt="image" src="https://github.com/user-attachments/assets/3cd8579b-3bc5-41cf-b668-ebb18fd84d9d" />

<img width="1365" height="649" alt="image" src="https://github.com/user-attachments/assets/06fb531c-6ccd-4c9b-b27f-c2bf1c7e18f8" />

<img width="1352" height="697" alt="image" src="https://github.com/user-attachments/assets/fe9c636f-ed95-4a54-932d-a9fa146d2ef5" />

<img width="1362" height="612" alt="image" src="https://github.com/user-attachments/assets/f46a67fc-e1fa-4df3-838f-a81e9cedae81" />

<img width="1353" height="707" alt="image" src="https://github.com/user-attachments/assets/572191c5-743c-441b-b35b-d5d1a3a54f1d" />

<img width="1353" height="694" alt="image" src="https://github.com/user-attachments/assets/f2e9cad5-4f00-475b-bdd7-4ad6d120359c" />

<img width="1340" height="692" alt="image" src="https://github.com/user-attachments/assets/a4402f21-130a-4c57-aa93-701940bec919" />

## Developer Blog
* v26.3.10 : I’m really excited to test this GraphQL API, so I built this one to try it out. So far, so good. I’m really impressed that the data updates are nearly instant (Whenever I change a Wikidata item label, it changes instantly in the GraphQL API. In contrast, when I use the SPARQL-based API endpoint, I notice some delays). My question is: can we increase the limit from 50 items? The GraphQL endpoint still can’t completely replace the SPARQL-based endpoint if it is limited to only 50.
* v26.3.12 : "Just to be sure, you can get more than 50 items, just not all at once. We have pagination built into the API"
  * I tried to query ‘instance of human’ (P31–Q5) in GraphQL using pagination, but since the hasNextPage result is empty, I can’t paginate further.
  * Update: If I just ignore the emptiness of hasNextPage and simply ask for more items using the endCursor, it works fine. The problem is that it doesn’t know when to stop. If the user keeps asking for more items using this trick, it will eventually loop back to the first items that were already queried before and never end.
  * Update: endCursor will return null once it reaches the last page. So we can use that to signal that pagination has reached the final page. Even if hasNextPage doesn’t work, we can use endCursor as a workaround.


