# refactoring
From Pittayut's COVID-19Tracker - RitoruX code: https://github.com/RitoruX/COVID-19-Tracker
## initialize() Method
in `/src/TrackerApp/AllStatsController.java`

https://github.com/RitoruX/COVID-19-Tracker/blob/master/src/TrackerApp/AllStatsController.java

Consider this code :

```java
public void initialize(URL url, ResourceBundle resourceBundle) {
        WorldAPILoader worldAPILoader = new WorldAPILoader();
        data = worldAPILoader.getCountry();
        StatsTable.setItems(data);
        Recovered.setCellValueFactory(new PropertyValueFactory<>("recovered"));
        Infected.setCellValueFactory(new PropertyValueFactory<>("infected"));
        CountryName.setCellValueFactory(new PropertyValueFactory<>("country"));
        Death.setCellValueFactory(new PropertyValueFactory<>("death"));
        Hospitalized.setCellValueFactory(new PropertyValueFactory<>("hospitalize"));
        TodayDeath.setCellValueFactory(new PropertyValueFactory<>("todayDeath"));
        TodayInfected.setCellValueFactory(new PropertyValueFactory<>("todayInfected"));
        MoreInfo.setCellValueFactory(new PropertyValueFactory<>("button"));
        Exit.setOnAction(this::exitHandler);
    }
```

- Refactoring Sign :

  - duplicated setCellValueFactory method
 
- Refactoring : Create array and loop to setCellValueFactory

```java
public void initialize(URL url, ResourceBundle resourceBundle) {
        WorldAPILoader worldAPILoader = new WorldAPILoader();
        data = worldAPILoader.getCountry();
        StatsTable.setItems(data);
        TableColumn<? ,?>[] column = {Recovered, Infected, CountryName, Death, Hospitalized, TodayDeath, TodayInfected, MoreInfo};
        String[] property = {"recovered", "infected", "country", "death", "hospitalize", "todayDeath", "todayInfected", "button"};
        for(int i = 0; i < column.lenght; i++;){
            cloumn[i].setCellValueFactory(new PropertyValueFactory<>(property[i]));
        }
        Exit.setOnAction(this::exitHandler);
    }

```
