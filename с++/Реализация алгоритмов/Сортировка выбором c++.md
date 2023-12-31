```c++
template<typename iter_type, typename compare_type>
void selection_sort(iter_type begin, iter_type end, compare_type comp) {
    using value_type = std::decay_t<decltype(*iter_type())>;

    // Если compare_type - указатель на функцию, ничего не произойдёт
    // Если compare_type - лямбда, она станет указателем на функцию
    // Если compare_type - что-то другое или функция с не правильными входными/выходными данными, будет ошибка
    bool (*_comp)(value_type, value_type) =  comp;

    iter_type i = begin;
    iter_type j = begin;

    while (i != end) {
        for (;j != end; j++) {
            if (_comp(*j, *i)) {
                std::swap(*j, *i);
            }
        }
        i++;
        j = i;
    }
}
```