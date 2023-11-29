```c++
template<typename iter_type, typename compare_type>
void insertion_sort(iter_type begin, iter_type end, compare_type comp) {
    using value_type = std::decay_t<decltype(*iter_type())>;

    // Если compare_type - указатель на функцию, ничего не произойдёт
    // Если compare_type - лямбда, она станет указателем на функцию
    // Если compare_type - что-то другое или функция с не правильными входными/выходными данными, будет ошибка
    bool (*_comp)(value_type, value_type) =  comp;

    for (iter_type it = begin; it != end;) {
        if (it == begin || *it > it[-1]) {
            it++;
        } else {
            std::swap(*it, it[-1]);
            it--;
        }
    }
}
```
