# Description
When you receive **500** status code with the description **Internal Server Error** in the API request.

# Cause
When <code class="expression">space.vars.SITENAME</code> server encounters some unexpected condition that prevents API request to be fulfilled, then this error will come. One of the probable causes of that issue can be unexpected headers in the API request.

# Solution
Please refer to the **Headers** in [Forming calls with <code class="expression">space.vars.SITENAME</code> API](forming-calls-with-api.md#explanation) for all possible valid headers in the API requests.
