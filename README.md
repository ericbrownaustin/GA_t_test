# GA_t_test
Simple script to pull Google Analytics events and perform t-test on single metric values


```
library(RGA)
library(data.table)

start.date <- "yyyy-mm-dd"
end.date <- "yyyy-mm-dd"

test_data <- get_ga(view_id,
                       start.date,
                       end.date,
                       metrics = "ga:transactionRevenue",
                       dimensions = "session_dimension,ga:eventLabel",
                       filters = "test_category_dimension")

setDT(test_data)

test_data_out <- dcast(test_data, session_dimension~eventLabel)

t.test(test_data_out$`ga_eventLabel[1]`, test_data_out$`ga_event_Label[2]`)
```
