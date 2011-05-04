XPathQuery
===

Reflecting the manner in which I use XML, my solution will have two functions declared as follows:

    NSArray *PerformXMLXPathQuery(NSData *document, NSString *query);
    NSArray *PerformHTMLXPathQuery(NSData *document, NSString *query);

For an entire XML document, contained in the NSData object "document", this function executes the XPath query in the NSString "query" and returns an NSArray of NSDictionary node objects for nodes that match the query.

The only difference between the two listed functions is that the the first expects proper XML data and the second expects HTML data.

Each result in the array of nodes returned will be an NSDictionary with the following structure:

- **nodeName** — an NSString containing the name of the node
- **nodeContent** — an NSString containing the textual content of the node
- **nodeAttributeArray** — an NSArray of NSDictionary where each dictionary has two keys: attributeName (NSString) and nodeContent (NSString)
- **nodeChildArray** — an NSArray of child nodes (same structure as this node)

Any of these fields may absent if not found in the libxml2 result.

If you don't know how or why to use an XPath query on an XML document, please look at my previous post titled [A Cocoa application driven by HTTP data](http://cocoawithlove.com/2008/09/cocoa-application-driven-by-http-data.html) which shows how XPath queries can be used to extract specific sections of data from an HTML document.