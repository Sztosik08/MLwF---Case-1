Na początku dane zostały sprawdzone pod kątem braków i nieprawidłowości – okazało się, że zbiór jest kompletny i nie wymaga imputacji. 

Następnie podzieliłem dane na trzy części: treningową (60%), walidacyjną (20%) i testową (20%), przy zachowaniu rzeczywistego rozkładu klas. 
Na zbiorze treningowym przeprowadziłem standaryzację, a potem redukcję wymiarów metodą PCA, zachowując 95% wariancji. Pozwoliło to uprościć strukturę danych i przyspieszyć uczenie modeli.

Ponieważ dane były silnie niezbalansowane - przypadki fraudów stanowiły ułamek wszystkich obserwacji - zdecydowałem się na częściowe zbilansowanie próbki treningowej do stosunku 1:20. 
Dzięki temu model miał więcej przykładów oszustw, ale proporcje nadal pozostały realistyczne. Walidacja i test zostały pozostawione w oryginalnych proporcjach, żeby ocena była wiarygodna.

W kolejnym kroku zbudowałem trzy modele: regresję logistyczną, las losowy i XGBoost. 
Wszystkie były trenowane na tych samych danych, a ich skuteczność oceniłem przy użyciu metryk dostosowanych do niezbalansowanych danych - głównie PR-AUC, F1-score, precision i recall. 
Spośród trzech modeli najlepsze wyniki osiągnął XGBoost, który uzyskał najwyższy PR-AUC (0.85) i F1-score (0.85), co oznacza, że najlepiej rozpoznawał transakcje oszukańcze przy zachowaniu wysokiej precyzji i niskiej liczby fałszywych alarmów.

Ostatecznie to XGBoost został wybrany jako model końcowy, ponieważ najskuteczniej uchwycił nieliniowe zależności w danych i najlepiej poradził sobie z problemem niezbalansowanych klas.
