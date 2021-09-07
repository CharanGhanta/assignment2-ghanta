# assignment2-ghanta
# SAI CHARAN GHANTA
##### vizag

Vizag, also known as **Visakhapatnam** is the largest city and the proposed administrative capital of the Indian state of Andhra Pradesh.It is also the most populated city of the state. It lies between the Eastern Ghats and the coast of the Bay of Bengal.It is the second largest city in the east coast of India after Chennai and also the fourth largest city in South India. It is one of the four smart cities of Andhra Pradesh selected under Smart Cities Mission.
It also serves as the headquarters of Visakhapatnam district.With an estimated output of $43.5 billion, the city is the **ninth largest contributor to India's overall Gross domestic product as of 2016**.In 2020, Visakhapatnam emerged as the finalist in the World Smart City Awards under Living and Inclusion category.

***

### Direction from Maryville To Vizag

1. Travel in a car from Maryville to Kansas City
2. Catch a flight from Kansas city to Washington
3. Then connecting flight from Washington to Delhi
4. Flight from Delhi to Vizag
    1. If connecting flight is missed, Book a new flight from Delhi to Vizag 
    2. We Can travel via Road or Railway Transport
5. Reached my favourite place

- Currency
    - Debit card
    - Credit Card
    - Gpay, Phonepay
- Camera
- Authentic wear
- Friends and Family
- Famous restaurants
- Navigation routes to Historic places and beaches

[Click this link to open my Aboutme File](https://github.com/CharanGhanta/assignment2-ghanta/blob/a131eab0e013c87dceaf6b93e65fc7839e228c0d/AboutMe.md)

***

### Markdown Tables are used to represent food and drinks

| Food Items | Locality | Price |  
| :---: | :---: | :---: |  
| Bamboo Chicken | Araku | $10 |  
| Madugula Halwa | Madugula | $6 |  
| Chicken maggi | Rushikonda | $3 |  
| Grilled Kebabs | RK beach | $5 |  

***

# MY quotes

> Love the life you live, Live the life you love. -*Bob Marley*

> Knowledge speaks but wisdom listens. *-Jimi Hendrix*

> Life is what happens when you're busy making other plans. -*John Lennon*

***

### Code Fencing

> A polygon is a plane figure that closes in a space using only line segments. If it must use only line segments and must close in a space, the polygon with the fewest sides has to be the triangle (three sides and interior angles).

[Link](https://tutors.com/math-tutors/geometry-help/what-is-a-polygon-definition-shapes#:~:text=Polygon%3B%20the%20word%20means%20%22many%20angles%2C%22%20but%20it,closes%20in%20a%20space%20using%20only%20line%20segments.)

[Link](https://cp-algorithms.com/geometry/minkowski.html)

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