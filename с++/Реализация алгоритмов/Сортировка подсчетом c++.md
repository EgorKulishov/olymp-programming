```c++
template<typename T>
void counting_sort(std::vector<T>& array) {
    T mx = array[0];
    T mn = array[0];
    for (T i : array) {
        if (i > mx) {
            mx = i;
        }
        if (i < mn) {
            mn = i;
        }
    }
    std::vector<T> count(mx - (mn - 1), T(0));

    for (T elem : array) {
        count[elem - mn]++;
    }

    T index = 0;
    for (size_t i = 0; i < mx - (mn - 1); i++) {
        for (T j = 0; j < count[i]; j++) {
            array[index] = i + mn;
            index++;
        }
    }
}
```