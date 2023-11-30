```c++
template<typename iter_type, typename compare_type>
void bubble_sort(iter_type begin, iter_type end, compare_type comp) {
    using value_type = std::decay_t<decltype(*iter_type())>;

    // Если compare_type - указатель на функцию, ничего не произойдёт
    // Если compare_type - лямбда, она станет указателем на функцию
    // Если compare_type - что-то другое или функция с не правильными входными/выходными данными, будет ошибка
    bool (*_comp)(value_type, value_type) =  comp; 

    bool sorted = false;
    while (!sorted) {
        sorted = true;
        iter_type i = begin;
        iter_type j = begin;
        j++;
        for (;j != end; i++, j++) {
            if (_comp(*j, *i)) {
                std::swap(*i, *j);
                sorted = false;
            }
        }
    }
}
```
