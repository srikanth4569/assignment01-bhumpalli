# assignment01-bhumpalli
# Srikanth Reddy Bhumpalli
### My Home in INDIA

My house is surrounded by beautiful fields there is no pollution in that area and its peaceful out there all the time and the most beautiful thing is i am with my **family** and **i am so happy when i am with them** and the people i know are also near to my house so when ever we have occasion  we all gather at one place and then celebrte 
***
**orderlist & unordered list**
1. Maryville to kansas city airport
2. kansas airport to ohare international airport chicago
3. chicago to rajiv gandhi interantional airport hyderabad
   1. hyderabad to vijaywada international airport
   2. book a cab from vijayawada airport to tadepalli ashramam road
4. from ashramam road by walk to house number 11 to reach my house .
*  cricket kit
*  tennis kit
   * wine
   * cards
   * food
*  cars to drive<br>

[click here to go to AboutMe](AboutMe.md)
***

**Table** <br>
The table is going to describe the types of drinks and where we can get them and the amount the customer should pay for the drinks they have purchased.<br>
| Drinks | Place | Amount To Pay |
| --- | --- | --- |
| Coke | Subway Maryville | $1 |
| Pepsi | Pizza Hut Maryville | $1 |
| Mojito | Kfc Maryville | $2 |
| Coffee | StarBucks Maryville | $3 |
***
**Pithy Quotes**
> If you are not willing to learn no one can help you.If you are determind to learn no one can stop you - *ZIG ZIGLAR*<br>
> A person who never made a mistake never tried anything new - *ALBERT EINSTEIN*
***
**Code Fencing**
> In geometry, the Minkowski sum (also known as dilation) of two sets of position vectors A and B in Euclidean space is formed by adding each vector in A to each vector in B, 
> i.e., the set {\displaystyle A+B=\{\mathbf {a} +\mathbf {b} \,|\,\mathbf {a} \in A,\ \mathbf {b} \in B\}.}A+B=\{\mathbf {a} +\mathbf {b} \,|\,\mathbf {a} \in A,\ \mathbf {b} \in > B\}.<br>
> **[Click here to go to source](https://en.wikipedia.org/wiki/Minkowski_addition)**
```
struct pt{
    long long x, y;
    pt operator + (const pt & p) const {
        return pt{x + p.x, y + p.y};
    }
    pt operator - (const pt & p) const {
        return pt{x - p.x, y - p.y};
    }
    long long cross(const pt & p) const {
        return x * p.y - y * p.x;
    }
};

void reorder_polygon(vector<pt> & P){
    size_t pos = 0;
    for(size_t i = 1; i < P.size(); i++){
        if(P[i].y < P[pos].y || (P[i].y == P[pos].y && P[i].x < P[pos].x))
            pos = i;
    }
    rotate(P.begin(), P.begin() + pos, P.end());
}

vector<pt> minkowski(vector<pt> P, vector<pt> Q){
    // the first vertex must be the lowest
    reorder_polygon(P);
    reorder_polygon(Q);
    // we must ensure cyclic indexing
    P.push_back(P[0]);
    P.push_back(P[1]);
    Q.push_back(Q[0]);
    Q.push_back(Q[1]);
    // main part
    vector<pt> result;
    size_t i = 0, j = 0;
    while(i < P.size() - 2 || j < Q.size() - 2){
        result.push_back(P[i] + Q[j]);
        auto cross = (P[i + 1] - P[i]).cross(Q[j + 1] - Q[j]);
        if(cross >= 0)
            ++i;
        if(cross <= 0)
            ++j;
    }
    return result;
}
```
**[Click here to view the source code](https://cp-algorithms.com/geometry/minkowski.html)**