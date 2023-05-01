library(httr)
library(rvest)
# Task 1
get_wiki_covid19_page <- function() {
    wiki_base_url <- "https://en.wikipedia.org/w/index.php"
    query_params<- list(title="Template:COVID-19_testing_by_country")
    wiki_response<- GET (wiki_base_url, query=query_params)
    return(wiki_response)
}

get_wiki_covid19_response<-get_wiki_covid19_page()
print(get_wiki_covid19_response)

#Task 2
# Get the root html node from the http response in task 1 
wiki_covid19_page_root_node <- read_html(get_wiki_covid19_response)
wiki_covid19_page_root_node 
# Get the table node from the root html node
table_node <- html_node(wiki_covid19_page_root_node, "table")
table_node 
# Read the table node and convert it into a data frame, and print the data frame for review
table_node<-html_table(table_node[2])
# there is an error coming up, saying that "Error in UseMethod("html_table"): no applicable method for 'html_table' applied to an object of class "list"
Traceback: 1. html_table(table_node[2])"
