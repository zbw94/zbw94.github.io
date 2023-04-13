query-properties:: [:cover :book-title :link :attachment :author]
#+BEGIN_QUERY
{:title [:h2 "Recently Read Book"]
 :query [:find (pull ?p [*])
         :where
         [_ :block/page ?p]
         [?p :block/properties ?prop]
         [(get ?prop :category) ?t]
         [(contains? ?t "book")]]
 :result-transform (fn [result] (sort-by (fn [h] (get h :block/updated-at)) result))
}
#+END_QUERY

-