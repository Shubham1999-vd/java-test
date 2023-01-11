# java-test

// Online Java Compiler
// Use this editor to write, compile and run your Java code online
import java.util.*;
class HelloWorld {
   
    public static void main(String[] args) {
      int WEEK_DAYS = 7;
      
      Scanner myObj = new Scanner(System.in);  
      int SubscriptionCost = myObj.nextInt();
      
      List<NewsPaper> newsPapers = new ArrayList<>();
      HashMap<String,String> map=new HashMap<String,String>();
      List<List<String>> result = new ArrayList<>();
      
      newsPapers.add(new NewsPaper("TOI", new double[]{3,3,3,3,3,5,6}));
      newsPapers.add(new NewsPaper("Hindu", new double[]{2.5,2.5,2.5,2.5,2.5,4,4}));
      newsPapers.add(new NewsPaper("ET", new double[]{4,4,4,4,4,4,10}));
      newsPapers.add(new NewsPaper("BM", new double[]{1.5,1.5,1.5,1.5,1.5,1.5,1.5}));
      newsPapers.add(new NewsPaper("HT", new double[]{2,2,2,2,2,4,4}));
      
     
      
      
      
      for(NewsPaper newsPaper : newsPapers) {
        
        List<String> affordable = new ArrayList<>();
        double totalCost = SubscriptionCost;
        
        if(newsPaper.getTotalCost() <= totalCost) {
          affordable.add(newsPaper.getName());
          totalCost -= newsPaper.getTotalCost();
        }
        
        for (int i = 0; i < newsPapers.size(); i++) {
          if(newsPapers.get(i).getName() != newsPaper.getName()) {
            if(newsPapers.get(i).getTotalCost() <= totalCost && map.get(newsPapers.get(i).getName()) != newsPaper.getName()) {
              affordable.add(newsPapers.get(i).getName());
              map.put(newsPaper.getName(), newsPapers.get(i).getName());
              totalCost -= newsPapers.get(i).getTotalCost();
              break;
            }
          }
        }
        
        if(affordable.size() > 1)
        result.add(affordable);
      }
      
      for(List<String> pair : result) {
        System.out.println(pair.toString());
      }
    
  }
  
}

class NewsPaper {
  private String name;
  private double cost[];
  
  
  public NewsPaper(String name, double[] cost) {
    this.name = name;
    this.cost = cost;
  }
  
  public double getTotalCost() {
    double sum = 0;
    for(int i = 0; i < cost.length; i++) {
      sum += cost[i];
    }
    
    return sum;
  }
  
  public void setCost(double[] cost) {
    this.cost = cost;
  }
  
  public double[] getCost() {
    return cost;
  }
  
  public void setName(String name) {
    this.name = name;
  }
  
  public String getName() {
    return name;
  }
}
