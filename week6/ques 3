#include <iostream>
#include <vector>
#include <unordered_map>
using namespace std;
class Graph {
    int V; 
    unordered_map<int, vector<int>> adjList; 
    bool isCyclicUtil(int v, vector<bool>& visited, vector<bool>& recStack);
public:
    Graph(int V); 
    void addEdge(int v, int w);
    bool isCyclic();
};
Graph::Graph(int V) {
    this->V = V;
}
void Graph::addEdge(int v, int w) {
    adjList[v].push_back(w);
}
bool Graph::isCyclicUtil(int v, vector<bool>& visited, vector<bool>& recStack) {
    if (!visited[v]) {
        visited[v] = true;
        recStack[v] = true;
        for (int neighbour : adjList[v]) {
            if (!visited[neighbour] && isCyclicUtil(neighbour, visited, recStack)) {
                return true;
            } else if (recStack[neighbour]) {
                return true;
            }
        }
    }
    recStack[v] = false; 
    return false;
}
bool Graph::isCyclic() {
    vector<bool> visited(V, false);
    vector<bool> recStack(V, false);
    for (int i = 0; i < V; i++) {
        if (isCyclicUtil(i, visited, recStack)) {
            return true;
        }
    }
    return false;
}
int main() {
    Graph g(6);
    g.addEdge(0, 1);
    g.addEdge(1, 2);
    g.addEdge(2, 0);
    g.addEdge(3, 4);
    g.addEdge(4, 5);
    g.addEdge(5, 3);
    if (g.isCyclic()) {
        cout << "Yes Cycle Exists" << endl;
    } else {
        cout << "No Cycle Exists" << endl;
    }
    return 0;
}
