<p>
<pre><code>
-- Start
-- Get the most recent date from a list 
-- I created a simple SAQL query:
q = load "Invoices";
q = foreach q generate 'Week_Ending_Date__c_sec_epoch' as 'CurrWeek';
q = order q by 'CurrWeek' desc;
q = limit q 1;
<p/>
-- And then use the above query to set up a filter (bind to the filter)
-- so that the filter has the most recent date
-- And I bound my main query to that
q = filter q by 'Week_Ending_Date__c_sec_epoch' == {{cell(Get_Current_Week_1.result, 0, \"CurrWeek\").asString()}}

-- End
</code></pre>
</p>
