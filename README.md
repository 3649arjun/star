
import 'package:ecommerceapp/search.dart';

import 'package:ecommerceapp/slides/sidebar.dart';
import 'package:ecommerceapp/slides/category.dart';
import 'package:ecommerceapp/slides/slides.dart';
import 'package:flutter/material.dart';
import 'package:font_awesome_flutter/font_awesome_flutter.dart';
import 'package:google_fonts/google_fonts.dart';

class homepage extends StatefulWidget {
  const homepage({Key? key}) : super(key: key);

  @override
  State<homepage> createState() => _homepageState();
}

class _homepageState extends State<homepage> {
  int _selectedIndex = 0;
  List<Widget>bottomitems=[
    homepage(),
    category(),
  ];
  @override
  Widget build(BuildContext context) {
    return SafeArea(
      child: Scaffold(
        drawer: sidebar(),
        backgroundColor: Colors.white,
        appBar: AppBar(

            iconTheme: IconThemeData(color: Colors.black),

          backgroundColor: Colors.white,

          title: RichText(

            text: TextSpan(
              text: 'A',
              style:GoogleFonts.lobsterTwo(
                fontSize: 25,

                fontStyle: FontStyle.italic,
                color : Color(0xff2e8b57),
              ),
                children: <TextSpan>[
                  TextSpan(
                      text: 'rvi',
              style: GoogleFonts.lobsterTwo(
                fontSize: 25,

                  fontStyle: FontStyle.italic,
                  color : Color(0xff2e8b57),

              ),

                  )

                ]
            ),
          ),
          actions: <Widget>[
            IconButton(onPressed: (){ showSearch(context: context, delegate: customsearch());}, icon: Icon(FontAwesomeIcons.search),color: Colors.black,iconSize: 20,),
            IconButton(onPressed: (){}, icon: Icon(FontAwesomeIcons.bell),color: Colors.black,iconSize: 20,),
            IconButton(onPressed: (){}, icon: Icon(FontAwesomeIcons.heart),color: Colors.black,iconSize: 20,),
            IconButton(onPressed: (){}, icon: Icon(FontAwesomeIcons.shoppingBag),color: Colors.black,iconSize: 20,)

          ],
          elevation:0.0,
      ),

      body:

          Container(
            padding: EdgeInsets.only(top: 20.0),
            child: ListView(
              scrollDirection: Axis.vertical,
              children: [
                Container(
                    padding:
                    EdgeInsets.symmetric(horizontal: 24.0, vertical: 32.0),

                    width: MediaQuery.of(context).size.width,
                    height: 400.0,
                    decoration: BoxDecoration(
                      color: Colors.white,

                      image:  DecorationImage(
                        image: AssetImage('assets/bigdress.jpg'),



                        fit: BoxFit.cover,
                      ),


                    )),
                    SizedBox(height: 10,),

                    slides(),
                    SizedBox(height: 20,),

              ],
            ),

      ),

        bottomNavigationBar: BottomNavigationBar(
          elevation: 0,
          onTap: (index){
            setState(() {
              _selectedIndex =index;
            });

          },
          backgroundColor: Colors.white,
          items:<BottomNavigationBarItem> [

            BottomNavigationBarItem(icon: Icon(FontAwesomeIcons.tshirt),label: 'Home',),
            BottomNavigationBarItem(icon: Icon(FontAwesomeIcons.diceFour,),label: 'Category',),
            BottomNavigationBarItem(icon: Icon(FontAwesomeIcons.user),label: 'profile'),

          ],
          currentIndex: _selectedIndex,
          selectedItemColor: Colors.black,
          unselectedItemColor:Colors.grey ,

        ),

      ),

    );
  }
}
