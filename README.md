# HashMap-Store-by-values

/*
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */

/**
 *
 * @author NetworkAcademy
 */
import java.util.Collections;
import java.util.Comparator;
import java.util.HashMap;
import java.util.Iterator;
import java.util.LinkedHashMap;
import java.util.LinkedList;
import java.util.List;
import java.util.Map;
import java.util.Set;
public class HashMapSortingByValues {
    public static void main(String[] args) {
        HashMap<Integer, String> hmap = new HashMap<Integer, String>();
        hmap.put(12, "XX");
        hmap.put(17, "YY");
        hmap.put(2, "AB");
        hmap.put(20, "XXZY");
        Set set = hmap.entrySet();
        Iterator iter = set.iterator();
        while(iter.hasNext()) {
            Map.Entry mentry = (Map.Entry)iter.next();
            System.out.println("Key is : " +mentry.getKey() + ", Value :" + mentry.getValue());
        }
        Map<Integer,String> map=sortByValues(hmap);
        System.out.println("after");
        Set set2=map.entrySet();
        Iterator ite2=set2.iterator();
        while(ite2.hasNext()){
            Map.Entry me2=(Map.Entry)ite2.next();
             System.out.println("Key is : " +me2.getKey() + ", Value :" + me2.getValue());
            
            
        }
    }
    private static HashMap sortByValues(HashMap map) { 
       List list = new LinkedList(map.entrySet());
       Collections.sort(list, new Comparator() {
            public int compare(Object o1, Object o2) {
               return ((Comparable) ((Map.Entry) (o1)).getValue())
                  .compareTo(((Map.Entry) (o2)).getValue());
            }
       });
    
    HashMap sortedHashMap = new LinkedHashMap();
       for (Iterator it = list.iterator(); it.hasNext();) {
              Map.Entry entry = (Map.Entry) it.next();
              sortedHashMap.put(entry.getKey(), entry.getValue());
       } 
       return sortedHashMap;
  }
}
