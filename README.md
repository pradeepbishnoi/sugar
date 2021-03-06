This library is a wrapper on android's db interface for SQLLite.. It is built for #in50hrs competition.

## Current State

#table creation

final String CREATE_TABLE_COUNTRIES =  "CREATE TABLE tbl_countries ("  + "id INTEGER PRIMARY KEY AUTOINCREMENT,"  + "country_name TEXT);";

final String CREATE_TABLE_STATES =  "CREATE TABLE tbl_states ("  + "id INTEGER PRIMARY KEY AUTOINCREMENT,"  + "state_name TEXT);";

db.execSQL(CREATE_TABLE_COUNTRIES);
db.execSQL(CREATE_TABLE_STATES);

# inserting values

ContentValues values = new ContentValues();
values.put("country_name", "India");
db.insert("tbl_countries", null, values);

## With Sugar

#table creation

public class Country extends SugarRecord<Country>{
    String countryName;

     public Country(Context context, String countryName){
            super(context);
            this.countryName = countryName;
     }
}

# inserting values

Country country = new Country(context, "India");
country.save();

# query

Country.findById(context, Country.class, 1);
Country.find(context, Country.class, "country_name=?", new String[]{"India"});

# delete
Country country = Country.findById(context, Country.class, 1);
country.delete();

# few more..

Country.listAll(context, Country.class);
Country.deleteAll(context, Country.class);


Example project:
Note Manager
https://github.com/satyan/SugarExample

Please visit the wiki section for more details.