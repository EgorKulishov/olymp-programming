```c++
struct Vertex {
    /*
    Какие-то данные
    */

    // Вешины в которые мы можем попасть из этой
    std::vector<int> neighbors; // или std::vector<Vertex*> neighbors

    // Были ли мы в этой вершине
    bool was = false;
};

void _dfs(int initial, std::vector<Vertex>& graph) {
    graph[initial].was = true;
    for (int neighbor : graph[initial].neighbors) {
        if (!graph[neighbor].was) {
            _dfs(neighbor, graph);

            /*
            Ещё что-то делаем, если надо
            */
        }
    }
}

void dfs(int initial, std::vector<Vertex>& graph) {
    //Запускаем DFS 
    _dfs(initial, graph);

    /* Если надо проверить граф на связность
    bool linked = true;
    for (Vertex vertex : graph) {
        if (vertex.was) {
            vertex.was = false;
        } else {
            linked = false;
        }
    }
    return linked;
    */

    // Возвращаем всё как было
    for (Vertex vertex : graph) {
        vertex.was = false;
    }
}
```