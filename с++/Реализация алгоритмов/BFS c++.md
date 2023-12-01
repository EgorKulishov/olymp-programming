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

void bfs(int initial, std::vector<Vertex> graph) {
    std::queue<int> vertex_queue;
    vertex_queue.push(initial);
    graph[initial].was = true;

    while (!vertex_queue.empty()) {
        int current = vertex_queue.front();
        vertex_queue.pop();

        for (int neighbor : graph[current].neighbors) {
            if (!graph[neighbor].was) {
                vertex_queue.push(neighbor);

                // Нужно именно после добавления вешины в очередь для того, чтобы эту вершину, как соседа другой вершины, не добавили в очередь повторно 
                graph[neighbor].was = true; 
            }
            /*
            Ещё что-то делаем, если надо
            */
        }
    }
    /* Если если нужно проверить граф на связность
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