# assignment2-sakhamuri
# Sai Lakshmi Kundana
###### Hyderabad
I spent 8 years of my life growing up in Hyderabad.My parents still live there.Most my memories growing up are attached to this city.
**Self Respect**
---
### Travel Guide To Hyderabad
1. Day 01
   1. Reach Kansas Airport(MCI).
   2. Take a flight to Chicago(ORD).
2. Day 02
   1. From Chicago, take a direct flight to Hyderabad.
* Sunscreen Lotion
* Medicines if you are allaergic to spices
* Documents needed while travelling out of country
  * Visa Copy
  * Passport
  * Indian Currency
* Video Recording Camera
[Navigate to AboutMe file](AboutMe.md)
---
### Best Food in Hyderabad
Must try food in Hyderabad
| Food/Drink  | Location  | Price |
|   :---:     |   :---:   | :---: |
| Biryani     | Paradise  | 400INR|
| Falooda     |LassiCorner| 100INR|
| MuttonPaya  | Chichas   | 300INR|
|DoubleKaMeeta| Vasireddy | 100INR|
---
### Fav Quotes
> Some people are worth melting for. — *Olaf, Frozen* <br>
> All our dreams can come true, if we have the courage to pursue them. — *Walt Disney*
---
### Algorithm
> Several algorithms for finding cycles quickly and with little memory are known. Robert W. Floyd's tortoise and hare algorithm moves two pointers at different speeds through the sequence of values until they both point to equal values.
[WikiLink](https://en.wikipedia.org/wiki/Cycle_detection)
```
int n;
vector<vector<int>> adj;
vector<char> color;
vector<int> parent;
int cycle_start, cycle_end;

bool dfs(int v) {
    color[v] = 1;
    for (int u : adj[v]) {
        if (color[u] == 0) {
            parent[u] = v;
            if (dfs(u))
                return true;
        } else if (color[u] == 1) {
            cycle_end = v;
            cycle_start = u;
            return true;
        }
    }
    color[v] = 2;
    return false;
}

void find_cycle() {
    color.assign(n, 0);
    parent.assign(n, -1);
    cycle_start = -1;

    for (int v = 0; v < n; v++) {
        if (color[v] == 0 && dfs(v))
            break;
    }

    if (cycle_start == -1) {
        cout << "Acyclic" << endl;
    } else {
        vector<int> cycle;
        cycle.push_back(cycle_start);
        for (int v = cycle_end; v != cycle_start; v = parent[v])
            cycle.push_back(v);
        cycle.push_back(cycle_start);
        reverse(cycle.begin(), cycle.end());

        cout << "Cycle found: ";
        for (int v : cycle)
            cout << v << " ";
        cout << endl;
    }
}
```
[QuickLink](https://cp-algorithms.com/graph/finding-cycle.html)