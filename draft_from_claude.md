
classDiagram
  class Customer {
    +String name
    +List~Cart~ purchaseHistory
  }
  class MenuItem {
    +String name
    +float price
    +Category category
    +float popularityRating
  }
  class Category {
    <<enumeration></enumeration>>
    DRINKS
    DESSERTS
    MAINS
  }
  class Menu {
    +List~MenuItem~ items
    +filterByCategory(Category category) List~MenuItem~
  }
  class Cart {
    +Customer customer
    +Map~MenuItem, int~ items
    +computeTotalCost() float
  }

  Customer "1" --> "0..*" Cart : places / history
  Cart "0..*" --> "0..*" MenuItem : contains
  Menu "1" --> "0..*" MenuItem : lists
  MenuItem --> Category
