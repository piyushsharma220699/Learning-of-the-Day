
Pagination refers to **the practice of dividing a large amount of content into separate pages**, with each page containing a specific number of items or pieces of information. It is commonly used on websites and in printed materials such as books, magazines, and newspapers to make it easier for users to navigate through the content and find what they are looking for. Pagination typically includes page numbers and navigation buttons or links to move between pages.

**The content can be paged in the following ways:**
1. Infinite Load Page
2. 'Load More' Page
3. Basic Page Number Page
4. Alphabetical Page
5. Date-Based Page

### Benefits of Pagination

- Improved Website Speed
- Better Engagement due to improved User Experience
- Better SEO

### Disadvantages of Pagination

1.  Inconsistent Data Retrieval: 
	Pagination relies on a consistent and predictable ordering of data. However, if the underlying data changes while the user is navigating through the pages, the order of items may become inconsistent, and the user may miss important data.

2. Reduced User Experience: 
	Pagination can lead to a poor user experience, especially when the user has to navigate through multiple pages to find what they are looking for. This can be frustrating and time-consuming, and users may abandon the site or lose interest.

### Limit Offset Pagination

Limit offset pagination is a technique used to limit the number of results returned from a database query and provide a way to paginate through the results. It works by specifying a limit for the number of results to return and an offset for the starting point of the results.

	https://localhost:8000/api/news?limit=10&offset=20
	The above link is similar to :  SELECT \* FROM News LIMIT 10 OFFSET 0;

For example, if you have a database table with 100 records and you want to display 10 records per page, you would set the limit to 10 and the offset to 0 for the first page, 10 for the second page, and so on.

### Page Number Pagination

In this technique, the data is divided into pages, and each page contains a fixed number of items. Users can navigate through the pages using page numbers or navigation buttons.

	https://localhost:8000/api/news?page=10

Here, we only specify the page number in the URL since the page size is fixed always and is configured in the backend.

Links ::
- https://developers.google.com/search/docs/specialty/ecommerce/pagination-and-incremental-page-loading#:~:text=Pagination%3A%20Where%20a%20user%20can,of%20results%20at%20a%20time.