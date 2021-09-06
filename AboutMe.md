# Komali Priyadarshini Myla

Born and raised in Andhra Pradesh, INDIA. Academic qualification is Bachelor's Degree.<br>
Work Experience with DELL EMC and Unisys, Bangalore, INDIA<br>
Moved to USA for Edcuation. Currently pursuing Master's at Northwest Missouri State.<br>

![Santa Cruz](Assignment02_KomaliMyla/Santa Cruz.jpg)

*****
# Drinks I Would Recommend

Below are the list of alocholic and non-alcoholic drinks that I would like to recommend because I prefer them all the time.

| Drink Name |        Where              |     Price    |
| ---------- | --------------------------| -------------|
| Margarita  | At any Bar                |  3 $         |
| Mojito     | At any Bar                |  6-14 $      |
| Wine       | At any Bar and Stores     |  15 - 34 $   |
| Coffee     | At any Cafe               |  2 - 5 $     |


******
# Quotes that I Like
 > Broken hearts and tears build you into a stronger person - *Bridgett Devoue*<br>
   She remembered who she was and the game changed  - *Lalah Deliah*<br>
   Never regret anything that made you smile        - *Mark Twain*<br>


*****
# Convex Hull construction using Graham's Scan
> Graham's Scan Algorithm is an efficient algorithm for finding the convex hull of a finite set of points in the plane with time complexity O(N log N). The algorithm finds all vertices of the convex hull ordered along its boundary. It uses a stack to detect and remove concavities in the boundary efficiently.
<https://iq.opengenus.org/graham-scan-convex-hull/#:~:text=Graham's%20Scan%20Algorithm%20is%20an,concavities%20in%20the%20boundary%20efficiently>

```
struct pt {
    double x, y;
};

bool cmp(pt a, pt b) {
    return a.x < b.x || (a.x == b.x && a.y < b.y);
}

bool cw(pt a, pt b, pt c) {
    return a.x*(b.y-c.y)+b.x*(c.y-a.y)+c.x*(a.y-b.y) < 0;
}

bool ccw(pt a, pt b, pt c) {
    return a.x*(b.y-c.y)+b.x*(c.y-a.y)+c.x*(a.y-b.y) > 0;
}

void convex_hull(vector<pt>& a) {
    if (a.size() == 1)
        return;

    sort(a.begin(), a.end(), &cmp);
    pt p1 = a[0], p2 = a.back();
    vector<pt> up, down;
    up.push_back(p1);
    down.push_back(p1);
    for (int i = 1; i < (int)a.size(); i++) {
        if (i == a.size() - 1 || cw(p1, a[i], p2)) {
            while (up.size() >= 2 && !cw(up[up.size()-2], up[up.size()-1], a[i]))
                up.pop_back();
            up.push_back(a[i]);
        }
        if (i == a.size() - 1 || ccw(p1, a[i], p2)) {
            while(down.size() >= 2 && !ccw(down[down.size()-2], down[down.size()-1], a[i]))
                down.pop_back();
            down.push_back(a[i]);
        }
    }

    a.clear();
    for (int i = 0; i < (int)up.size(); i++)
        a.push_back(up[i]);
    for (int i = down.size() - 2; i > 0; i--)
        a.push_back(down[i]);
}
```
Code Source : <https://cp-algorithms.com/geometry/grahams-scan-convex-hull.html>


