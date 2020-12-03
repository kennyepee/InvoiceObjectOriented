# InvoiceObjectOriented
package com.company;
import java.util.ArrayList;
import java.util.Scanner;
public class Main {

    public static void main(String[] args) {

        ArrayList<Inventory> productsinstock = new ArrayList<Inventory>();


        Inventory ts = new Inventory();
        ts.setInvproducts("Bison Sweater");
        ts.setInvprices(55.99);
        productsinstock.add(ts);

        ts = new Inventory();
        ts.setInvproducts("Bison Tee");
        ts.setInvprices(14.99);
        productsinstock.add(ts);

        ts = new Inventory();
        ts.setInvproducts("Bison Hoodie");
        ts.setInvprices(23.99);
        productsinstock.add(ts);


        ts = new Inventory();
        ts.setInvproducts("Bison Bumpersticker");
        ts.setInvprices(4.99);
        productsinstock.add(ts);

        String answer = "";

        ArrayList<Purchases> purchaselist = new ArrayList<Purchases>();
        Scanner input = new Scanner(System.in);
        double price;
        price = 0.00;


        do {
            System.out.println("What do you want to do?");
            System.out.println("1) add purchase 2) change purchase 3) show purchases 4) finish transaction");
            answer = input.nextLine();

            if (answer.equals("1")) {
                System.out.println("What do you wish to buy?");
                answer = input.nextLine();


                for (int i = 0; i < productsinstock.size(); i++) {
                    if (answer.equals(productsinstock.get(i).getInvproducts())){
                      price = productsinstock.get(i).getInvprices();
                    }
                }
                Purchases pts = new Purchases();
                pts.setPurchproduct(answer);
                pts.setPurchprice(price);
                purchaselist.add(pts);

            }  else if (answer.equals("2")) {
                System.out.println("What do you wish to remove?");
                for (int i = 0; i < purchaselist.size(); i++) {
                    System.out.println(purchaselist.get(i).getPurchproduct());
                }

                String delete = input.nextLine();
                int position = -1;
                for (int i = 0; i < purchaselist.size(); i++) {
                    if (purchaselist.get(i).getPurchproduct().equals(delete)) ;
                    {
                        position = i;
                    }

                    if (position != -1) {
                        purchaselist.remove(position);
                    }
                }

            }else if (answer.equals("3")) {
                System.out.println("Here are your purchases");
                for (int i = 0; i < purchaselist.size(); i++) {
                    System.out.println(purchaselist.get(i).getPurchproduct());

                }

            }

        } while (! answer.equals("4"));
        double totalcost = 0.0;
        for (int i = 0; i < purchaselist.size() ; i++)
        {
            totalcost += purchaselist.get(i).getPurchprice();

        }
        System.out.println("Your order total is: $" + totalcost);
        System.out.println("Thank you for ordering!");

    }
}



//        }
//    for (int i = 0; i < productsinstock.size(); i++){
//
//        product = productsinstock.get(0).getInvproducts();
//        price = productsinstock.get(0).getInvprices();
//        System.out.println(product + " - " + price);
//                }
//
//    }
//}
