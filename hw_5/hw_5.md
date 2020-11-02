WITH MEMBER Measures.[Promotion Percentage] AS
    '(Measures.[Promotion Sales] / Measures.[Store Sales])'
SELECT
    {
        Time.[2013].[Q3]:[Q4].CHILDREN,
        Time.[2014].[Q1].CHILDREN
    } ON 0,
    FILTER (
        {Store.[Store Name].MEMBERS}, Measures.[Promotion Percentage] <= 0.1
    ) ON 1
FROM Sales
WHERE (
    Measures.[Unit Sales],
    Product.[Brand Name].Guinness,
    Store.USA.OR
)
