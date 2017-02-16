
#include <a_samp>
#include <a_mysql>
#include <zcmd>
#include <YSI\y_ini>
#include <foreach>
#include <sscanf2>
#include <streamer>
#include <fader>
мурат хуй

//#define DIALOG_REGISTER 1
//#define DIALOG_LOGIN 2
//#define DIALOG_SUCCESS_1 3
//#define DIALOG_SUCCESS_2 4
#define DIALOG_DRUGSNGUNS 5
#define DIALOG_LOCKER 6
#define DIALOG_USE 7
#define DIALOG_STATS 8
#define DIALOG_COMMANDS 9
#define DIALOG_ANIMS 10
#define DIALOG_DRUGS 12
#define DIALOG_BUY 13
#define DIALOG_TRAIN 14
#define DIALOG_AGE 2009
#define DIALOG_RACE 2010
#define DIALOG_GENDER 2011

#define DIALOG_BOOMBOX  800
#define DIALOG_BOOMBOX1 801
#define DIALOG_BOOMBOX2 802
#define DIALOG_BOOMBOX3 803
#define DIALOG_BOOMBOX4 804
#define DIALOG_BOOMBOX5 805
#define DIALOG_BOOMBOX6 806
#define DIALOG_BOOMBOX7 807

#define MAX_BUSINESSES 500

#define COLOR_GRAD6 0xF0F0F0FF
#define COLOR_GREY 0xAFAFAFAA
#define COLOR_GREEN 0x008000FF
#define COLOR_WHITE 0xFFFFFFFF

#define PATH "/users/%s.ini"
#define BPATH "/business/%i.ini"
#define HPATH "/houses/%i.ini"

//=========================SETTINGS=========================

#undef MAX_PLAYERS
#define MAX_PLAYERS 50

#define MAX_DVEHICLES 500
#define MAX_DEALERSHIPS 10
#define MAX_FUEL_STATIONS 10

#define VEHICLE_FILE_PATH "AVS/Vehicles/"
#define DEALERSHIP_FILE_PATH "AVS/Dealerships/"
#define FUEL_STATION_FILE_PATH "AVS/FuelStations/"

#define MAX_PLAYER_VEHICLES 3
#define FUEL_PRICE 1
#define GAS_CAN_PRICE 50
#define ALARM_TIME 10000  // alarm duration in milliseconds (1 second = 1000 milliseconds)
#define DEFAULT_NUMBER_PLATE "un-registered"

//==========================================================


#define GivePlayerArmour(%1,%2) SetPlayerArmour(%1,floatadd(GetArmour(%1),%2))

#define ResetMoneyBar ResetPlayerMoney
#define UpdateMoneyBar GivePlayerMoney

#define COL_WHITE 		"{FFFFFF}"
#define COL_RED 		"{F81414}"
#define COL_GREEN 		"{00FF22}"
#define COL_LIGHTBLUE 	"{00CED1}"
#define COLORYELLOW 	"{9DBD1E}"
#define COLORORANGE 	"{E68C0E}"
#define COLORBLUE   	"{39AACC}"
#define COLORGREEN 		"{6FA828}"
#define COLORWHITE  	"{FFFFFF}"
#define COLORRED    	"{FF0000}"
#define COLORGREY   	"{7D8584}"
#define COL_BROWN       "{6B3F34}"
#define COL_PROPERTIES  "{4364FF}"
#define COL_HOUSES      "{6200FF}"

#define BALLAS 0
#define GROVE 1
#define VAGOS 2
#define AZTECAS 3
#define RIFA 4

#define L_MAX_COUNT 105

#define COLOR_GROVE 0x51A505FF
#define COLOR_SEVILLE 0xBCFB84FF
#define COLOR_AZTECAS 0x00BBBBFF
#define COLOR_VAGOS 0xFFFF24FF
#define COLOR_BALLAS 0xB000B0FF
#define COLOR_LSPD 0x5353FFFF
#define COLOR_ADMIN 0xFD7E00FF

#define COLOR_GOLD 	0xF6C861AA
#define COLOR_RED 0xA10000AA
#define COLOR_DARKRED 0xCD000000
#define COLOR_LIGHTRED 0xFF6347AA
#define COLOR_LIGHTBLUE 0x33CCFFAA
#define COLOR_LIGHTGREEN 0x9ACD32AA
#define COLOR_LIGHTRED 0xFF6347AA
#define COLOR_LIGHTBLUE 0x33CCFFAA
#define COLOR_LIGHTBLUE2 0x0080FFAA
#define COLOR_LIGHTGREEN 0x9ACD32AA
#define COLOR_LIGHTORANGE 0xFF8000FF
#define COLOR_DARKBROWN 0xB36C42FF
#define COLOR_MEDIUMBLUE 0x1ED5C7FF
#define COLOR_LIGHTYELLOW 0xE0E377AA
#define COLOR_LIGHTYELLOW2 0xE0EA64AA
#define COLOR_LIGHTYELLOW3 0xFF6347AA
#define COLOR_DARKPURPLE 0x5F56F8AA
#define COLOR_YELLOW 0xFFFF00AA
#define COLOR_YELLOW2 0xF5DEB3AA
#define COLOR_FADE1 0xE6E6E6E6
#define COLOR_FADE2 0xC8C8C8C8
#define COLOR_FADE3 0xAAAAAAAA
#define COLOR_FADE4 0x8C8C8C8C
#define COLOR_FADE5 0x6E6E6E6E
#define COLOR_PURPLE 0xC2A2DAAA
#define COLOR_OOC 0xE0FFFFAA

#define VEHICLE_DEALERSHIP 1
#define VEHICLE_PLAYER 2
#define ShowErrorDialog(%1,%2) ShowPlayerDialog(%1, COLOR_LIGHTRED, DIALOG_STYLE_MSGBOX, "ERROR", %2, "OK", "")
#define COLOR_ADVERTISEMENT 0xFF2BD500

#define SCM SendClientMessage


enum pInfo
{
    pPass,
    pCash,
    pAdmin,
    pKills,
    pDeaths,
    dLSD,
    dCocaine,
    dMarijuana,
    pRespect,
    pCigarettes,
    pBankAccount,
    pAccountdata,
    pBeer,
    Float:pHealth,
    pNumber,
    pSkin,
    pWeapon1,
    pAmmo1,
    pWeapon2,
    pAmmo2,
    pWeapon3,
	pAmmo3,
	pWeapon4,
	pAmmo4,
	pWeapon5,
	pAmmo5,
	pWeapon6,
	pAmmo6,
	pWeapon7,
	pAmmo7,
	pWeapon8,
	pAmmo8,
	pWeapon9,
	pAmmo9,
	pWeapon10,
	pAmmo10,
	pWeapon11,
	pAmmo11,
	pWeapon12,
	pAmmo12,
	pWeapon13,
	pAmmo13,
	pWeapon14,
	pAmmo14,
	BizID,
	HouseID,
	pLevel,
	BusinessMoney,
	pDriverLicense,
	pAge,
	pGender,
	pInJail,
	pInJailTime,
	pMask,
	pFightingStyle,
	pBoombox,
	Float:pXPos,
	Float:pYPos,
	Float:pZPos,
	pInterior,
	pVirtualWorld,
 	pBanned,
    BannedIP[22],
    pExperience,
	dSeeds,
	dWater
}

// 2241
// 630
// 2010
enum bInfo
{
    bOwned,
    bPrice,
    bOwner[MAX_PLAYER_NAME],
    bType,
    bLocked,
    bMoney,
    Float:bEntranceX,
    Float:bEntranceY,
    Float:bEntranceZ,
    Float:bEntranceA,
    Float:bExitX,
    Float:bExitY,
    Float:bExitZ,
    Float:bExitA,
    bInt,
    bWorld,
    bInsideInt,
    bInsideWorld,
    bInsideIcon,
    bOutsideIcon,
	Text3D: DLabel,
    bName[128]
}

enum hInfo
{
    hOwned,
    hPrice,
    hOwner[MAX_PLAYER_NAME],
    hLocked,
    hMoney,
    Float:hEntranceX,
    Float:hEntranceY,
    Float:hEntranceZ,
    Float:hEntranceA,
    Float:hExitX,
    Float:hExitY,
    Float:hExitZ,
    Float:hExitA,
    hInt,
    hWorld,
    hInsideInt,
    hInsideWorld,
    hInsideIcon,
    hOutsideIcon,
	Text3D: hDLabel,
}

enum weapons
{
    Melee,
    Thrown,
    Pistols,
    Shotguns,
    SubMachine,
    Assault,
    Rifles,
    Heavy,
    Handheld
}

enum
{
	DIALOG_NONE=12345,
	DIALOG_ERROR=12346,
	DIALOG_VEHICLE=500,
	DIALOG_VEHICLE_BUY,
	DIALOG_VEHICLE_SELL,
	DIALOG_FINDVEHICLE,
	DIALOG_TRUNK,
	DIALOG_TRUNK_ACTION,
	DIALOG_VEHICLE_PLATE,
	DIALOG_FUEL,
	DIALOG_EDITVEHICLE
};

new maintimer;
new speedotimer;
new savetimer;

new SaveVehicleIndex;

new RefuelTime[MAX_PLAYERS];
new TrackCar[MAX_PLAYERS];
new DialogReturn[MAX_PLAYERS];

//new Text:SpeedoBox;
new Text:SpeedoText[MAX_PLAYERS];

new Float:Fuel[MAX_VEHICLES] = {100.0, ...};
new VehicleSecurity[MAX_VEHICLES];

new VehicleCreated[MAX_DVEHICLES];
new VehicleID[MAX_DVEHICLES];
new VehicleModel[MAX_DVEHICLES];
new Float:VehiclePos[MAX_DVEHICLES][4];
new VehicleColor[MAX_DVEHICLES][2];
new VehicleInterior[MAX_DVEHICLES];
new VehicleWorld[MAX_DVEHICLES];
new VehicleOwner[MAX_DVEHICLES][MAX_PLAYER_NAME];
new VehicleNumberPlate[MAX_DVEHICLES][16];
new VehicleValue[MAX_DVEHICLES];
new VehicleLock[MAX_DVEHICLES];
new VehicleAlarm[MAX_DVEHICLES];
new VehicleTrunk[MAX_DVEHICLES][5][2];
new VehicleMods[MAX_DVEHICLES][14];
new VehiclePaintjob[MAX_DVEHICLES] = {255, ...};
new Text3D:VehicleLabel[MAX_DVEHICLES];

new DealershipCreated[MAX_DEALERSHIPS];
new Float:DealershipPos[MAX_DEALERSHIPS][3];
new Text3D:DealershipLabel[MAX_DEALERSHIPS];

new FuelStationCreated[MAX_FUEL_STATIONS];
new Float:FuelStationPos[MAX_FUEL_STATIONS][3];
new Text3D:FuelStationLabel[MAX_FUEL_STATIONS];

new VehicleNames[][] = {
	"Landstalker","Bravura","Buffalo","Linerunner","Perennial","Sentinel","Dumper","Firetruck","Trashmaster","Stretch","Manana","Infernus",
	"Voodoo","Pony","Mule","Cheetah","Ambulance","Leviathan","Moonbeam","Esperanto","Taxi","Washington","Bobcat","Mr Whoopee","BF Injection",
	"Hunter","Premier","Enforcer","Securicar","Banshee","Predator","Bus","Rhino","Barracks","Hotknife","Trailer","Previon","Coach","Cabbie",
	"Stallion","Rumpo","RC Bandit","Romero","Packer","Monster","Admiral","Squalo","Seasparrow","Pizzaboy","Tram","Trailer","Turismo","Speeder",
	"Reefer","Tropic","Flatbed","Yankee","Caddy","Solair","Berkley's RC Van","Skimmer","PCJ-600","Faggio","Freeway","RC Baron","RC Raider",
	"Glendale","Oceanic","Sanchez","Sparrow","Patriot","Quad","Coastguard","Dinghy","Hermes","Sabre","Rustler","ZR3 50","Walton","Regina",
	"Comet","BMX","Burrito","Camper","Marquis","Baggage","Dozer","Maverick","News Chopper","Rancher","FBI Rancher","Virgo","Greenwood",
	"Jetmax","Hotring","Sandking","Blista Compact","Police Maverick","Boxville","Benson","Mesa","RC Goblin","Hotring Racer A","Hotring Racer B",
	"Bloodring Banger","Rancher","Super GT","Elegant","Journey","Bike","Mountain Bike","Beagle","Cropdust","Stunt","Tanker","RoadTrain",
	"Nebula","Majestic","Buccaneer","Shamal","Hydra","FCR-900","NRG-500","HPV1000","Cement Truck","Tow Truck","Fortune","Cadrona","FBI Truck",
	"Willard","Forklift","Tractor","Combine","Feltzer","Remington","Slamvan","Blade","Freight","Streak","Vortex","Vincent","Bullet","Clover",
	"Sadler","Firetruck","Hustler","Intruder","Primo","Cargobob","Tampa","Sunrise","Merit","Utility","Nevada","Yosemite","Windsor","Monster A",
	"Monster B","Uranus","Jester","Sultan","Stratum","Elegy","Raindance","RC Tiger","Flash","Tahoma","Savanna","Bandito","Freight","Trailer",
	"Kart","Mower","Duneride","Sweeper","Broadway","Tornado","AT-400","DFT-30","Huntley","Stafford","BF-400","Newsvan","Tug","Trailer A","Emperor",
	"Wayfarer","Euros","Hotdog","Club","Trailer B","Trailer C","Andromada","Dodo","RC Cam","Launch","Police Car (LSPD)","Police Car (SFPD)",
	"Police Car (LVPD)","Police Ranger","Picador","S.W.A.T. Van","Alpha","Phoenix","Glendale","Sadler","Luggage Trailer A","Luggage Trailer B",
	"Stair Trailer","Boxville","Farm Plow","Utility Trailer"
};

enum MainZone
{
	Zone_Name[28],
	Float:Zone_Area[6]
}

static const SanAndreasZones[][MainZone] = {

	{"The Big Ear",	                {-410.00,1403.30,-3.00,-137.90,1681.20,200.00}},
	{"Aldea Malvada",               {-1372.10,2498.50,0.00,-1277.50,2615.30,200.00}},
	{"Angel Pine",                  {-2324.90,-2584.20,-6.10,-1964.20,-2212.10,200.00}},
	{"Arco del Oeste",              {-901.10,2221.80,0.00,-592.00,2571.90,200.00}},
	{"Avispa Country Club",         {-2646.40,-355.40,0.00,-2270.00,-222.50,200.00}},
	{"Avispa Country Club",         {-2831.80,-430.20,-6.10,-2646.40,-222.50,200.00}},
	{"Avispa Country Club",         {-2361.50,-417.10,0.00,-2270.00,-355.40,200.00}},
	{"Avispa Country Club",         {-2667.80,-302.10,-28.80,-2646.40,-262.30,71.10}},
	{"Avispa Country Club",         {-2470.00,-355.40,0.00,-2270.00,-318.40,46.10}},
	{"Avispa Country Club",         {-2550.00,-355.40,0.00,-2470.00,-318.40,39.70}},
	{"Back o Beyond",               {-1166.90,-2641.10,0.00,-321.70,-1856.00,200.00}},
	{"Battery Point",               {-2741.00,1268.40,-4.50,-2533.00,1490.40,200.00}},
	{"Bayside",                     {-2741.00,2175.10,0.00,-2353.10,2722.70,200.00}},
	{"Bayside Marina",              {-2353.10,2275.70,0.00,-2153.10,2475.70,200.00}},
	{"Beacon Hill",                 {-399.60,-1075.50,-1.40,-319.00,-977.50,198.50}},
	{"Blackfield",                  {964.30,1203.20,-89.00,1197.30,1403.20,110.90}},
	{"Blackfield",                  {964.30,1403.20,-89.00,1197.30,1726.20,110.90}},
	{"Blackfield Chapel",           {1375.60,596.30,-89.00,1558.00,823.20,110.90}},
	{"Blackfield Chapel",           {1325.60,596.30,-89.00,1375.60,795.00,110.90}},
	{"Blackfield Intersection",     {1197.30,1044.60,-89.00,1277.00,1163.30,110.90}},
	{"Blackfield Intersection",     {1166.50,795.00,-89.00,1375.60,1044.60,110.90}},
	{"Blackfield Intersection",     {1277.00,1044.60,-89.00,1315.30,1087.60,110.90}},
	{"Blackfield Intersection",     {1375.60,823.20,-89.00,1457.30,919.40,110.90}},
	{"Blueberry",                   {104.50,-220.10,2.30,349.60,152.20,200.00}},
	{"Blueberry",                   {19.60,-404.10,3.80,349.60,-220.10,200.00}},
	{"Blueberry Acres",             {-319.60,-220.10,0.00,104.50,293.30,200.00}},
	{"Caligula's Palace",           {2087.30,1543.20,-89.00,2437.30,1703.20,110.90}},
	{"Caligula's Palace",           {2137.40,1703.20,-89.00,2437.30,1783.20,110.90}},
	{"Calton Heights",              {-2274.10,744.10,-6.10,-1982.30,1358.90,200.00}},
	{"Chinatown",                   {-2274.10,578.30,-7.60,-2078.60,744.10,200.00}},
	{"City Hall",                   {-2867.80,277.40,-9.10,-2593.40,458.40,200.00}},
	{"Come-A-Lot",                  {2087.30,943.20,-89.00,2623.10,1203.20,110.90}},
	{"Commerce",                    {1323.90,-1842.20,-89.00,1701.90,-1722.20,110.90}},
	{"Commerce",                    {1323.90,-1722.20,-89.00,1440.90,-1577.50,110.90}},
	{"Commerce",                    {1370.80,-1577.50,-89.00,1463.90,-1384.90,110.90}},
	{"Commerce",                    {1463.90,-1577.50,-89.00,1667.90,-1430.80,110.90}},
	{"Commerce",                    {1583.50,-1722.20,-89.00,1758.90,-1577.50,110.90}},
	{"Commerce",                    {1667.90,-1577.50,-89.00,1812.60,-1430.80,110.90}},
	{"Conference Center",           {1046.10,-1804.20,-89.00,1323.90,-1722.20,110.90}},
	{"Conference Center",           {1073.20,-1842.20,-89.00,1323.90,-1804.20,110.90}},
	{"Cranberry Station",           {-2007.80,56.30,0.00,-1922.00,224.70,100.00}},
	{"Creek",                       {2749.90,1937.20,-89.00,2921.60,2669.70,110.90}},
	{"Dillimore",                   {580.70,-674.80,-9.50,861.00,-404.70,200.00}},
	{"Doherty",                     {-2270.00,-324.10,-0.00,-1794.90,-222.50,200.00}},
	{"Doherty",                     {-2173.00,-222.50,-0.00,-1794.90,265.20,200.00}},
	{"Downtown",                    {-1982.30,744.10,-6.10,-1871.70,1274.20,200.00}},
	{"Downtown",                    {-1871.70,1176.40,-4.50,-1620.30,1274.20,200.00}},
	{"Downtown",                    {-1700.00,744.20,-6.10,-1580.00,1176.50,200.00}},
	{"Downtown",                    {-1580.00,744.20,-6.10,-1499.80,1025.90,200.00}},
	{"Downtown",                    {-2078.60,578.30,-7.60,-1499.80,744.20,200.00}},
	{"Downtown",                    {-1993.20,265.20,-9.10,-1794.90,578.30,200.00}},
	{"Downtown Los Santos",         {1463.90,-1430.80,-89.00,1724.70,-1290.80,110.90}},
	{"Downtown Los Santos",         {1724.70,-1430.80,-89.00,1812.60,-1250.90,110.90}},
	{"Downtown Los Santos",         {1463.90,-1290.80,-89.00,1724.70,-1150.80,110.90}},
	{"Downtown Los Santos",         {1370.80,-1384.90,-89.00,1463.90,-1170.80,110.90}},
	{"Downtown Los Santos",         {1724.70,-1250.90,-89.00,1812.60,-1150.80,110.90}},
	{"Downtown Los Santos",         {1370.80,-1170.80,-89.00,1463.90,-1130.80,110.90}},
	{"Downtown Los Santos",         {1378.30,-1130.80,-89.00,1463.90,-1026.30,110.90}},
	{"Downtown Los Santos",         {1391.00,-1026.30,-89.00,1463.90,-926.90,110.90}},
	{"Downtown Los Santos",         {1507.50,-1385.20,110.90,1582.50,-1325.30,335.90}},
	{"East Beach",                  {2632.80,-1852.80,-89.00,2959.30,-1668.10,110.90}},
	{"East Beach",                  {2632.80,-1668.10,-89.00,2747.70,-1393.40,110.90}},
	{"East Beach",                  {2747.70,-1668.10,-89.00,2959.30,-1498.60,110.90}},
	{"East Beach",                  {2747.70,-1498.60,-89.00,2959.30,-1120.00,110.90}},
	{"East Los Santos",             {2421.00,-1628.50,-89.00,2632.80,-1454.30,110.90}},
	{"East Los Santos",             {2222.50,-1628.50,-89.00,2421.00,-1494.00,110.90}},
	{"East Los Santos",             {2266.20,-1494.00,-89.00,2381.60,-1372.00,110.90}},
	{"East Los Santos",             {2381.60,-1494.00,-89.00,2421.00,-1454.30,110.90}},
	{"East Los Santos",             {2281.40,-1372.00,-89.00,2381.60,-1135.00,110.90}},
	{"East Los Santos",             {2381.60,-1454.30,-89.00,2462.10,-1135.00,110.90}},
	{"East Los Santos",             {2462.10,-1454.30,-89.00,2581.70,-1135.00,110.90}},
	{"Easter Basin",                {-1794.90,249.90,-9.10,-1242.90,578.30,200.00}},
	{"Easter Basin",                {-1794.90,-50.00,-0.00,-1499.80,249.90,200.00}},
	{"Easter Bay Airport",          {-1499.80,-50.00,-0.00,-1242.90,249.90,200.00}},
	{"Easter Bay Airport",          {-1794.90,-730.10,-3.00,-1213.90,-50.00,200.00}},
	{"Easter Bay Airport",          {-1213.90,-730.10,0.00,-1132.80,-50.00,200.00}},
	{"Easter Bay Airport",          {-1242.90,-50.00,0.00,-1213.90,578.30,200.00}},
	{"Easter Bay Airport",          {-1213.90,-50.00,-4.50,-947.90,578.30,200.00}},
	{"Easter Bay Airport",          {-1315.40,-405.30,15.40,-1264.40,-209.50,25.40}},
	{"Easter Bay Airport",          {-1354.30,-287.30,15.40,-1315.40,-209.50,25.40}},
	{"Easter Bay Airport",          {-1490.30,-209.50,15.40,-1264.40,-148.30,25.40}},
	{"Easter Bay Chemicals",        {-1132.80,-768.00,0.00,-956.40,-578.10,200.00}},
	{"Easter Bay Chemicals",        {-1132.80,-787.30,0.00,-956.40,-768.00,200.00}},
	{"El Castillo del Diablo",      {-464.50,2217.60,0.00,-208.50,2580.30,200.00}},
	{"El Castillo del Diablo",      {-208.50,2123.00,-7.60,114.00,2337.10,200.00}},
	{"El Castillo del Diablo",      {-208.50,2337.10,0.00,8.40,2487.10,200.00}},
	{"El Corona",                   {1812.60,-2179.20,-89.00,1970.60,-1852.80,110.90}},
	{"El Corona",                   {1692.60,-2179.20,-89.00,1812.60,-1842.20,110.90}},
	{"El Quebrados",                {-1645.20,2498.50,0.00,-1372.10,2777.80,200.00}},
	{"Esplanade East",              {-1620.30,1176.50,-4.50,-1580.00,1274.20,200.00}},
	{"Esplanade East",              {-1580.00,1025.90,-6.10,-1499.80,1274.20,200.00}},
	{"Esplanade East",              {-1499.80,578.30,-79.60,-1339.80,1274.20,20.30}},
	{"Esplanade North",             {-2533.00,1358.90,-4.50,-1996.60,1501.20,200.00}},
	{"Esplanade North",             {-1996.60,1358.90,-4.50,-1524.20,1592.50,200.00}},
	{"Esplanade North",             {-1982.30,1274.20,-4.50,-1524.20,1358.90,200.00}},
	{"Fallen Tree",                 {-792.20,-698.50,-5.30,-452.40,-380.00,200.00}},
	{"Fallow Bridge",               {434.30,366.50,0.00,603.00,555.60,200.00}},
	{"Fern Ridge",                  {508.10,-139.20,0.00,1306.60,119.50,200.00}},
	{"Financial",                   {-1871.70,744.10,-6.10,-1701.30,1176.40,300.00}},
	{"Fisher's Lagoon",             {1916.90,-233.30,-100.00,2131.70,13.80,200.00}},
	{"Flint Intersection",          {-187.70,-1596.70,-89.00,17.00,-1276.60,110.90}},
	{"Flint Range",                 {-594.10,-1648.50,0.00,-187.70,-1276.60,200.00}},
	{"Fort Carson",                 {-376.20,826.30,-3.00,123.70,1220.40,200.00}},
	{"Foster Valley",               {-2270.00,-430.20,-0.00,-2178.60,-324.10,200.00}},
	{"Foster Valley",               {-2178.60,-599.80,-0.00,-1794.90,-324.10,200.00}},
	{"Foster Valley",               {-2178.60,-1115.50,0.00,-1794.90,-599.80,200.00}},
	{"Foster Valley",               {-2178.60,-1250.90,0.00,-1794.90,-1115.50,200.00}},
	{"Frederick Bridge",            {2759.20,296.50,0.00,2774.20,594.70,200.00}},
	{"Gant Bridge",                 {-2741.40,1659.60,-6.10,-2616.40,2175.10,200.00}},
	{"Gant Bridge",                 {-2741.00,1490.40,-6.10,-2616.40,1659.60,200.00}},
	{"Ganton",                      {2222.50,-1852.80,-89.00,2632.80,-1722.30,110.90}},
	{"Ganton",                      {2222.50,-1722.30,-89.00,2632.80,-1628.50,110.90}},
	{"Garcia",                      {-2411.20,-222.50,-0.00,-2173.00,265.20,200.00}},
	{"Garcia",                      {-2395.10,-222.50,-5.30,-2354.00,-204.70,200.00}},
	{"Garver Bridge",               {-1339.80,828.10,-89.00,-1213.90,1057.00,110.90}},
	{"Garver Bridge",               {-1213.90,950.00,-89.00,-1087.90,1178.90,110.90}},
	{"Garver Bridge",               {-1499.80,696.40,-179.60,-1339.80,925.30,20.30}},
	{"Glen Park",                   {1812.60,-1449.60,-89.00,1996.90,-1350.70,110.90}},
	{"Glen Park",                   {1812.60,-1100.80,-89.00,1994.30,-973.30,110.90}},
	{"Glen Park",                   {1812.60,-1350.70,-89.00,2056.80,-1100.80,110.90}},
	{"Green Palms",                 {176.50,1305.40,-3.00,338.60,1520.70,200.00}},
	{"Greenglass College",          {964.30,1044.60,-89.00,1197.30,1203.20,110.90}},
	{"Greenglass College",          {964.30,930.80,-89.00,1166.50,1044.60,110.90}},
	{"Hampton Barns",               {603.00,264.30,0.00,761.90,366.50,200.00}},
	{"Hankypanky Point",            {2576.90,62.10,0.00,2759.20,385.50,200.00}},
	{"Harry Gold Parkway",          {1777.30,863.20,-89.00,1817.30,2342.80,110.90}},
	{"Hashbury",                    {-2593.40,-222.50,-0.00,-2411.20,54.70,200.00}},
	{"Hilltop Farm",                {967.30,-450.30,-3.00,1176.70,-217.90,200.00}},
	{"Hunter Quarry",               {337.20,710.80,-115.20,860.50,1031.70,203.70}},
	{"Idlewood",                    {1812.60,-1852.80,-89.00,1971.60,-1742.30,110.90}},
	{"Idlewood",                    {1812.60,-1742.30,-89.00,1951.60,-1602.30,110.90}},
	{"Idlewood",                    {1951.60,-1742.30,-89.00,2124.60,-1602.30,110.90}},
	{"Idlewood",                    {1812.60,-1602.30,-89.00,2124.60,-1449.60,110.90}},
	{"Idlewood",                    {2124.60,-1742.30,-89.00,2222.50,-1494.00,110.90}},
	{"Idlewood",                    {1971.60,-1852.80,-89.00,2222.50,-1742.30,110.90}},
	{"Jefferson",                   {1996.90,-1449.60,-89.00,2056.80,-1350.70,110.90}},
	{"Jefferson",                   {2124.60,-1494.00,-89.00,2266.20,-1449.60,110.90}},
	{"Jefferson",                   {2056.80,-1372.00,-89.00,2281.40,-1210.70,110.90}},
	{"Jefferson",                   {2056.80,-1210.70,-89.00,2185.30,-1126.30,110.90}},
	{"Jefferson",                   {2185.30,-1210.70,-89.00,2281.40,-1154.50,110.90}},
	{"Jefferson",                   {2056.80,-1449.60,-89.00,2266.20,-1372.00,110.90}},
	{"Julius Thruway East",         {2623.10,943.20,-89.00,2749.90,1055.90,110.90}},
	{"Julius Thruway East",         {2685.10,1055.90,-89.00,2749.90,2626.50,110.90}},
	{"Julius Thruway East",         {2536.40,2442.50,-89.00,2685.10,2542.50,110.90}},
	{"Julius Thruway East",         {2625.10,2202.70,-89.00,2685.10,2442.50,110.90}},
	{"Julius Thruway North",        {2498.20,2542.50,-89.00,2685.10,2626.50,110.90}},
	{"Julius Thruway North",        {2237.40,2542.50,-89.00,2498.20,2663.10,110.90}},
	{"Julius Thruway North",        {2121.40,2508.20,-89.00,2237.40,2663.10,110.90}},
	{"Julius Thruway North",        {1938.80,2508.20,-89.00,2121.40,2624.20,110.90}},
	{"Julius Thruway North",        {1534.50,2433.20,-89.00,1848.40,2583.20,110.90}},
	{"Julius Thruway North",        {1848.40,2478.40,-89.00,1938.80,2553.40,110.90}},
	{"Julius Thruway North",        {1704.50,2342.80,-89.00,1848.40,2433.20,110.90}},
	{"Julius Thruway North",        {1377.30,2433.20,-89.00,1534.50,2507.20,110.90}},
	{"Julius Thruway South",        {1457.30,823.20,-89.00,2377.30,863.20,110.90}},
	{"Julius Thruway South",        {2377.30,788.80,-89.00,2537.30,897.90,110.90}},
	{"Julius Thruway West",         {1197.30,1163.30,-89.00,1236.60,2243.20,110.90}},
	{"Julius Thruway West",         {1236.60,2142.80,-89.00,1297.40,2243.20,110.90}},
	{"Juniper Hill",                {-2533.00,578.30,-7.60,-2274.10,968.30,200.00}},
	{"Juniper Hollow",              {-2533.00,968.30,-6.10,-2274.10,1358.90,200.00}},
	{"K.A.C.C. Military Fuels",     {2498.20,2626.50,-89.00,2749.90,2861.50,110.90}},
	{"Kincaid Bridge",              {-1339.80,599.20,-89.00,-1213.90,828.10,110.90}},
	{"Kincaid Bridge",              {-1213.90,721.10,-89.00,-1087.90,950.00,110.90}},
	{"Kincaid Bridge",              {-1087.90,855.30,-89.00,-961.90,986.20,110.90}},
	{"King's",                      {-2329.30,458.40,-7.60,-1993.20,578.30,200.00}},
	{"King's",                      {-2411.20,265.20,-9.10,-1993.20,373.50,200.00}},
	{"King's",                      {-2253.50,373.50,-9.10,-1993.20,458.40,200.00}},
	{"LVA Freight Depot",           {1457.30,863.20,-89.00,1777.40,1143.20,110.90}},
	{"LVA Freight Depot",           {1375.60,919.40,-89.00,1457.30,1203.20,110.90}},
	{"LVA Freight Depot",           {1277.00,1087.60,-89.00,1375.60,1203.20,110.90}},
	{"LVA Freight Depot",           {1315.30,1044.60,-89.00,1375.60,1087.60,110.90}},
	{"LVA Freight Depot",           {1236.60,1163.40,-89.00,1277.00,1203.20,110.90}},
	{"Las Barrancas",               {-926.10,1398.70,-3.00,-719.20,1634.60,200.00}},
	{"Las Brujas",                  {-365.10,2123.00,-3.00,-208.50,2217.60,200.00}},
	{"Las Colinas",                 {1994.30,-1100.80,-89.00,2056.80,-920.80,110.90}},
	{"Las Colinas",                 {2056.80,-1126.30,-89.00,2126.80,-920.80,110.90}},
	{"Las Colinas",                 {2185.30,-1154.50,-89.00,2281.40,-934.40,110.90}},
	{"Las Colinas",                 {2126.80,-1126.30,-89.00,2185.30,-934.40,110.90}},
	{"Las Colinas",                 {2747.70,-1120.00,-89.00,2959.30,-945.00,110.90}},
	{"Las Colinas",                 {2632.70,-1135.00,-89.00,2747.70,-945.00,110.90}},
	{"Las Colinas",                 {2281.40,-1135.00,-89.00,2632.70,-945.00,110.90}},
	{"Las Payasadas",               {-354.30,2580.30,2.00,-133.60,2816.80,200.00}},
	{"Las Venturas Airport",        {1236.60,1203.20,-89.00,1457.30,1883.10,110.90}},
	{"Las Venturas Airport",        {1457.30,1203.20,-89.00,1777.30,1883.10,110.90}},
	{"Las Venturas Airport",        {1457.30,1143.20,-89.00,1777.40,1203.20,110.90}},
	{"Las Venturas Airport",        {1515.80,1586.40,-12.50,1729.90,1714.50,87.50}},
	{"Last Dime Motel",             {1823.00,596.30,-89.00,1997.20,823.20,110.90}},
	{"Leafy Hollow",                {-1166.90,-1856.00,0.00,-815.60,-1602.00,200.00}},
	{"Liberty City",                {-1000.00,400.00,1300.00,-700.00,600.00,1400.00}},
	{"Lil' Probe Inn",              {-90.20,1286.80,-3.00,153.80,1554.10,200.00}},
	{"Linden Side",                 {2749.90,943.20,-89.00,2923.30,1198.90,110.90}},
	{"Linden Station",              {2749.90,1198.90,-89.00,2923.30,1548.90,110.90}},
	{"Linden Station",              {2811.20,1229.50,-39.50,2861.20,1407.50,60.40}},
	{"Little Mexico",               {1701.90,-1842.20,-89.00,1812.60,-1722.20,110.90}},
	{"Little Mexico",               {1758.90,-1722.20,-89.00,1812.60,-1577.50,110.90}},
	{"Los Flores",                  {2581.70,-1454.30,-89.00,2632.80,-1393.40,110.90}},
	{"Los Flores",                  {2581.70,-1393.40,-89.00,2747.70,-1135.00,110.90}},
	{"Los Santos International",    {1249.60,-2394.30,-89.00,1852.00,-2179.20,110.90}},
	{"Los Santos International",    {1852.00,-2394.30,-89.00,2089.00,-2179.20,110.90}},
	{"Los Santos International",    {1382.70,-2730.80,-89.00,2201.80,-2394.30,110.90}},
	{"Los Santos International",    {1974.60,-2394.30,-39.00,2089.00,-2256.50,60.90}},
	{"Los Santos International",    {1400.90,-2669.20,-39.00,2189.80,-2597.20,60.90}},
	{"Los Santos International",    {2051.60,-2597.20,-39.00,2152.40,-2394.30,60.90}},
	{"Marina",                      {647.70,-1804.20,-89.00,851.40,-1577.50,110.90}},
	{"Marina",                      {647.70,-1577.50,-89.00,807.90,-1416.20,110.90}},
	{"Marina",                      {807.90,-1577.50,-89.00,926.90,-1416.20,110.90}},
	{"Market",                      {787.40,-1416.20,-89.00,1072.60,-1310.20,110.90}},
	{"Market",                      {952.60,-1310.20,-89.00,1072.60,-1130.80,110.90}},
	{"Market",                      {1072.60,-1416.20,-89.00,1370.80,-1130.80,110.90}},
	{"Market",                      {926.90,-1577.50,-89.00,1370.80,-1416.20,110.90}},
	{"Market Station",              {787.40,-1410.90,-34.10,866.00,-1310.20,65.80}},
	{"Martin Bridge",               {-222.10,293.30,0.00,-122.10,476.40,200.00}},
	{"Missionary Hill",             {-2994.40,-811.20,0.00,-2178.60,-430.20,200.00}},
	{"Montgomery",                  {1119.50,119.50,-3.00,1451.40,493.30,200.00}},
	{"Montgomery",                  {1451.40,347.40,-6.10,1582.40,420.80,200.00}},
	{"Montgomery Intersection",     {1546.60,208.10,0.00,1745.80,347.40,200.00}},
	{"Montgomery Intersection",     {1582.40,347.40,0.00,1664.60,401.70,200.00}},
	{"Mulholland",                  {1414.00,-768.00,-89.00,1667.60,-452.40,110.90}},
	{"Mulholland",                  {1281.10,-452.40,-89.00,1641.10,-290.90,110.90}},
	{"Mulholland",                  {1269.10,-768.00,-89.00,1414.00,-452.40,110.90}},
	{"Mulholland",                  {1357.00,-926.90,-89.00,1463.90,-768.00,110.90}},
	{"Mulholland",                  {1318.10,-910.10,-89.00,1357.00,-768.00,110.90}},
	{"Mulholland",                  {1169.10,-910.10,-89.00,1318.10,-768.00,110.90}},
	{"Mulholland",                  {768.60,-954.60,-89.00,952.60,-860.60,110.90}},
	{"Mulholland",                  {687.80,-860.60,-89.00,911.80,-768.00,110.90}},
	{"Mulholland",                  {737.50,-768.00,-89.00,1142.20,-674.80,110.90}},
	{"Mulholland",                  {1096.40,-910.10,-89.00,1169.10,-768.00,110.90}},
	{"Mulholland",                  {952.60,-937.10,-89.00,1096.40,-860.60,110.90}},
	{"Mulholland",                  {911.80,-860.60,-89.00,1096.40,-768.00,110.90}},
	{"Mulholland",                  {861.00,-674.80,-89.00,1156.50,-600.80,110.90}},
	{"Mulholland Intersection",     {1463.90,-1150.80,-89.00,1812.60,-768.00,110.90}},
	{"North Rock",                  {2285.30,-768.00,0.00,2770.50,-269.70,200.00}},
	{"Ocean Docks",                 {2373.70,-2697.00,-89.00,2809.20,-2330.40,110.90}},
	{"Ocean Docks",                 {2201.80,-2418.30,-89.00,2324.00,-2095.00,110.90}},
	{"Ocean Docks",                 {2324.00,-2302.30,-89.00,2703.50,-2145.10,110.90}},
	{"Ocean Docks",                 {2089.00,-2394.30,-89.00,2201.80,-2235.80,110.90}},
	{"Ocean Docks",                 {2201.80,-2730.80,-89.00,2324.00,-2418.30,110.90}},
	{"Ocean Docks",                 {2703.50,-2302.30,-89.00,2959.30,-2126.90,110.90}},
	{"Ocean Docks",                 {2324.00,-2145.10,-89.00,2703.50,-2059.20,110.90}},
	{"Ocean Flats",                 {-2994.40,277.40,-9.10,-2867.80,458.40,200.00}},
	{"Ocean Flats",                 {-2994.40,-222.50,-0.00,-2593.40,277.40,200.00}},
	{"Ocean Flats",                 {-2994.40,-430.20,-0.00,-2831.80,-222.50,200.00}},
	{"Octane Springs",              {338.60,1228.50,0.00,664.30,1655.00,200.00}},
	{"Old Venturas Strip",          {2162.30,2012.10,-89.00,2685.10,2202.70,110.90}},
	{"Palisades",                   {-2994.40,458.40,-6.10,-2741.00,1339.60,200.00}},
	{"Palomino Creek",              {2160.20,-149.00,0.00,2576.90,228.30,200.00}},
	{"Paradiso",                    {-2741.00,793.40,-6.10,-2533.00,1268.40,200.00}},
	{"Pershing Square",             {1440.90,-1722.20,-89.00,1583.50,-1577.50,110.90}},
	{"Pilgrim",                     {2437.30,1383.20,-89.00,2624.40,1783.20,110.90}},
	{"Pilgrim",                     {2624.40,1383.20,-89.00,2685.10,1783.20,110.90}},
	{"Pilson Intersection",         {1098.30,2243.20,-89.00,1377.30,2507.20,110.90}},
	{"Pirates in Men's Pants",      {1817.30,1469.20,-89.00,2027.40,1703.20,110.90}},
	{"Playa del Seville",           {2703.50,-2126.90,-89.00,2959.30,-1852.80,110.90}},
	{"Prickle Pine",                {1534.50,2583.20,-89.00,1848.40,2863.20,110.90}},
	{"Prickle Pine",                {1117.40,2507.20,-89.00,1534.50,2723.20,110.90}},
	{"Prickle Pine",                {1848.40,2553.40,-89.00,1938.80,2863.20,110.90}},
	{"Prickle Pine",                {1938.80,2624.20,-89.00,2121.40,2861.50,110.90}},
	{"Queens",                      {-2533.00,458.40,0.00,-2329.30,578.30,200.00}},
	{"Queens",                      {-2593.40,54.70,0.00,-2411.20,458.40,200.00}},
	{"Queens",                      {-2411.20,373.50,0.00,-2253.50,458.40,200.00}},
	{"Randolph Industrial",         {1558.00,596.30,-89.00,1823.00,823.20,110.90}},
	{"Redsands East",               {1817.30,2011.80,-89.00,2106.70,2202.70,110.90}},
	{"Redsands East",               {1817.30,2202.70,-89.00,2011.90,2342.80,110.90}},
	{"Redsands East",               {1848.40,2342.80,-89.00,2011.90,2478.40,110.90}},
	{"Redsands West",               {1236.60,1883.10,-89.00,1777.30,2142.80,110.90}},
	{"Redsands West",               {1297.40,2142.80,-89.00,1777.30,2243.20,110.90}},
	{"Redsands West",               {1377.30,2243.20,-89.00,1704.50,2433.20,110.90}},
	{"Redsands West",               {1704.50,2243.20,-89.00,1777.30,2342.80,110.90}},
	{"Regular Tom",                 {-405.70,1712.80,-3.00,-276.70,1892.70,200.00}},
	{"Richman",                     {647.50,-1118.20,-89.00,787.40,-954.60,110.90}},
	{"Richman",                     {647.50,-954.60,-89.00,768.60,-860.60,110.90}},
	{"Richman",                     {225.10,-1369.60,-89.00,334.50,-1292.00,110.90}},
	{"Richman",                     {225.10,-1292.00,-89.00,466.20,-1235.00,110.90}},
	{"Richman",                     {72.60,-1404.90,-89.00,225.10,-1235.00,110.90}},
	{"Richman",                     {72.60,-1235.00,-89.00,321.30,-1008.10,110.90}},
	{"Richman",                     {321.30,-1235.00,-89.00,647.50,-1044.00,110.90}},
	{"Richman",                     {321.30,-1044.00,-89.00,647.50,-860.60,110.90}},
	{"Richman",                     {321.30,-860.60,-89.00,687.80,-768.00,110.90}},
	{"Richman",                     {321.30,-768.00,-89.00,700.70,-674.80,110.90}},
	{"Robada Intersection",         {-1119.00,1178.90,-89.00,-862.00,1351.40,110.90}},
	{"Roca Escalante",              {2237.40,2202.70,-89.00,2536.40,2542.50,110.90}},
	{"Roca Escalante",              {2536.40,2202.70,-89.00,2625.10,2442.50,110.90}},
	{"Rockshore East",              {2537.30,676.50,-89.00,2902.30,943.20,110.90}},
	{"Rockshore West",              {1997.20,596.30,-89.00,2377.30,823.20,110.90}},
	{"Rockshore West",              {2377.30,596.30,-89.00,2537.30,788.80,110.90}},
	{"Rodeo",                       {72.60,-1684.60,-89.00,225.10,-1544.10,110.90}},
	{"Rodeo",                       {72.60,-1544.10,-89.00,225.10,-1404.90,110.90}},
	{"Rodeo",                       {225.10,-1684.60,-89.00,312.80,-1501.90,110.90}},
	{"Rodeo",                       {225.10,-1501.90,-89.00,334.50,-1369.60,110.90}},
	{"Rodeo",                       {334.50,-1501.90,-89.00,422.60,-1406.00,110.90}},
	{"Rodeo",                       {312.80,-1684.60,-89.00,422.60,-1501.90,110.90}},
	{"Rodeo",                       {422.60,-1684.60,-89.00,558.00,-1570.20,110.90}},
	{"Rodeo",                       {558.00,-1684.60,-89.00,647.50,-1384.90,110.90}},
	{"Rodeo",                       {466.20,-1570.20,-89.00,558.00,-1385.00,110.90}},
	{"Rodeo",                       {422.60,-1570.20,-89.00,466.20,-1406.00,110.90}},
	{"Rodeo",                       {466.20,-1385.00,-89.00,647.50,-1235.00,110.90}},
	{"Rodeo",                       {334.50,-1406.00,-89.00,466.20,-1292.00,110.90}},
	{"Royal Casino",                {2087.30,1383.20,-89.00,2437.30,1543.20,110.90}},
	{"San Andreas Sound",           {2450.30,385.50,-100.00,2759.20,562.30,200.00}},
	{"Santa Flora",                 {-2741.00,458.40,-7.60,-2533.00,793.40,200.00}},
	{"Santa Maria Beach",           {342.60,-2173.20,-89.00,647.70,-1684.60,110.90}},
	{"Santa Maria Beach",           {72.60,-2173.20,-89.00,342.60,-1684.60,110.90}},
	{"Shady Cabin",                 {-1632.80,-2263.40,-3.00,-1601.30,-2231.70,200.00}},
	{"Shady Creeks",                {-1820.60,-2643.60,-8.00,-1226.70,-1771.60,200.00}},
	{"Shady Creeks",                {-2030.10,-2174.80,-6.10,-1820.60,-1771.60,200.00}},
	{"Sobell Rail Yards",           {2749.90,1548.90,-89.00,2923.30,1937.20,110.90}},
	{"Spinybed",                    {2121.40,2663.10,-89.00,2498.20,2861.50,110.90}},
	{"Starfish Casino",             {2437.30,1783.20,-89.00,2685.10,2012.10,110.90}},
	{"Starfish Casino",             {2437.30,1858.10,-39.00,2495.00,1970.80,60.90}},
	{"Starfish Casino",             {2162.30,1883.20,-89.00,2437.30,2012.10,110.90}},
	{"Temple",                      {1252.30,-1130.80,-89.00,1378.30,-1026.30,110.90}},
	{"Temple",                      {1252.30,-1026.30,-89.00,1391.00,-926.90,110.90}},
	{"Temple",                      {1252.30,-926.90,-89.00,1357.00,-910.10,110.90}},
	{"Temple",                      {952.60,-1130.80,-89.00,1096.40,-937.10,110.90}},
	{"Temple",                      {1096.40,-1130.80,-89.00,1252.30,-1026.30,110.90}},
	{"Temple",                      {1096.40,-1026.30,-89.00,1252.30,-910.10,110.90}},
	{"The Camel's Toe",             {2087.30,1203.20,-89.00,2640.40,1383.20,110.90}},
	{"The Clown's Pocket",          {2162.30,1783.20,-89.00,2437.30,1883.20,110.90}},
	{"The Emerald Isle",            {2011.90,2202.70,-89.00,2237.40,2508.20,110.90}},
	{"The Farm",                    {-1209.60,-1317.10,114.90,-908.10,-787.30,251.90}},
	{"Four Dragons Casino",         {1817.30,863.20,-89.00,2027.30,1083.20,110.90}},
	{"The High Roller",             {1817.30,1283.20,-89.00,2027.30,1469.20,110.90}},
	{"The Mako Span",               {1664.60,401.70,0.00,1785.10,567.20,200.00}},
	{"The Panopticon",              {-947.90,-304.30,-1.10,-319.60,327.00,200.00}},
	{"The Pink Swan",               {1817.30,1083.20,-89.00,2027.30,1283.20,110.90}},
	{"The Sherman Dam",             {-968.70,1929.40,-3.00,-481.10,2155.20,200.00}},
	{"The Strip",                   {2027.40,863.20,-89.00,2087.30,1703.20,110.90}},
	{"The Strip",                   {2106.70,1863.20,-89.00,2162.30,2202.70,110.90}},
	{"The Strip",                   {2027.40,1783.20,-89.00,2162.30,1863.20,110.90}},
	{"The Strip",                   {2027.40,1703.20,-89.00,2137.40,1783.20,110.90}},
	{"The Visage",                  {1817.30,1863.20,-89.00,2106.70,2011.80,110.90}},
	{"The Visage",                  {1817.30,1703.20,-89.00,2027.40,1863.20,110.90}},
	{"Unity Station",               {1692.60,-1971.80,-20.40,1812.60,-1932.80,79.50}},
	{"Valle Ocultado",              {-936.60,2611.40,2.00,-715.90,2847.90,200.00}},
	{"Verdant Bluffs",              {930.20,-2488.40,-89.00,1249.60,-2006.70,110.90}},
	{"Verdant Bluffs",              {1073.20,-2006.70,-89.00,1249.60,-1842.20,110.90}},
	{"Verdant Bluffs",              {1249.60,-2179.20,-89.00,1692.60,-1842.20,110.90}},
	{"Verdant Meadows",             {37.00,2337.10,-3.00,435.90,2677.90,200.00}},
	{"Verona Beach",                {647.70,-2173.20,-89.00,930.20,-1804.20,110.90}},
	{"Verona Beach",                {930.20,-2006.70,-89.00,1073.20,-1804.20,110.90}},
	{"Verona Beach",                {851.40,-1804.20,-89.00,1046.10,-1577.50,110.90}},
	{"Verona Beach",                {1161.50,-1722.20,-89.00,1323.90,-1577.50,110.90}},
	{"Verona Beach",                {1046.10,-1722.20,-89.00,1161.50,-1577.50,110.90}},
	{"Vinewood",                    {787.40,-1310.20,-89.00,952.60,-1130.80,110.90}},
	{"Vinewood",                    {787.40,-1130.80,-89.00,952.60,-954.60,110.90}},
	{"Vinewood",                    {647.50,-1227.20,-89.00,787.40,-1118.20,110.90}},
	{"Vinewood",                    {647.70,-1416.20,-89.00,787.40,-1227.20,110.90}},
	{"Whitewood Estates",           {883.30,1726.20,-89.00,1098.30,2507.20,110.90}},
	{"Whitewood Estates",           {1098.30,1726.20,-89.00,1197.30,2243.20,110.90}},
	{"Willowfield",                 {1970.60,-2179.20,-89.00,2089.00,-1852.80,110.90}},
	{"Willowfield",                 {2089.00,-2235.80,-89.00,2201.80,-1989.90,110.90}},
	{"Willowfield",                 {2089.00,-1989.90,-89.00,2324.00,-1852.80,110.90}},
	{"Willowfield",                 {2201.80,-2095.00,-89.00,2324.00,-1989.90,110.90}},
	{"Willowfield",                 {2541.70,-1941.40,-89.00,2703.50,-1852.80,110.90}},
	{"Willowfield",                 {2324.00,-2059.20,-89.00,2541.70,-1852.80,110.90}},
	{"Willowfield",                 {2541.70,-2059.20,-89.00,2703.50,-1941.40,110.90}},
	{"Yellow Bell Station",         {1377.40,2600.40,-21.90,1492.40,2687.30,78.00}},
	// Citys Zones
	{"Los Santos",                  {44.60,-2892.90,-242.90,2997.00,-768.00,900.00}},
	{"Las Venturas",                {869.40,596.30,-242.90,2997.00,2993.80,900.00}},
	{"Bone County",                 {-480.50,596.30,-242.90,869.40,2993.80,900.00}},
	{"Tierra Robada",               {-2997.40,1659.60,-242.90,-480.50,2993.80,900.00}},
	{"Tierra Robada",               {-1213.90,596.30,-242.90,-480.50,1659.60,900.00}},
	{"San Fierro",                  {-2997.40,-1115.50,-242.90,-1213.90,1659.60,900.00}},
	{"Red County",                  {-1213.90,-768.00,-242.90,2997.00,596.30,900.00}},
	{"Flint County",                {-1213.90,-2892.90,-242.90,44.60,-768.00,900.00}},
	{"Whetstone",                   {-2997.40,-2892.90,-242.90,-1213.90,-1115.50,900.00}}
};

forward MainTimer();
forward Speedometer();
forward SaveTimer();
forward StopAlarm(vehicleid);

new BusinessInfo[200][bInfo];
new HouseInfo[200][hInfo];
new PlayerInfo[MAX_PLAYERS][pInfo];

forward LoadUser_data(playerid,name[],value[]);
public LoadUser_data(playerid,name[],value[])
{
    INI_Int("Password",PlayerInfo[playerid][pPass]);
    INI_Int("Cash",PlayerInfo[playerid][pCash]);
    INI_Int("Admin",PlayerInfo[playerid][pAdmin]);
    INI_Int("Kills",PlayerInfo[playerid][pKills]);
    INI_Int("Deaths",PlayerInfo[playerid][pDeaths]);
    INI_Int("BizID",PlayerInfo[playerid][BizID]);
    INI_Int("LSD",PlayerInfo[playerid][dLSD]);
    INI_Int("Cocaine",PlayerInfo[playerid][dCocaine]);
    INI_Int("Marijuana",PlayerInfo[playerid][dMarijuana]);
    INI_Int("Respect",PlayerInfo[playerid][pRespect]);
    INI_Int("Cigarettes",PlayerInfo[playerid][pCigarettes]);
    INI_Int("Beer",PlayerInfo[playerid][pBeer]);
    INI_Int("BankAccount",PlayerInfo[playerid][pBankAccount]);
    INI_Int("Datasaved",PlayerInfo[playerid][pAccountdata]);
    INI_Int("Number",PlayerInfo[playerid][pNumber]);
    INI_Int("Level",PlayerInfo[playerid][pLevel]);
    INI_Int("Skin", PlayerInfo[playerid][pSkin]);
    INI_Int("HouseID", PlayerInfo[playerid][HouseID]);
    INI_Int("Weapon1",PlayerInfo[playerid][pWeapon1]);
    INI_Int("Weapon2",PlayerInfo[playerid][pWeapon2]);
    INI_Int("Weapon3",PlayerInfo[playerid][pWeapon3]);
    INI_Int("Weapon4",PlayerInfo[playerid][pWeapon4]);
    INI_Int("Weapon5",PlayerInfo[playerid][pWeapon5]);
    INI_Int("Weapon6",PlayerInfo[playerid][pWeapon6]);
    INI_Int("Weapon7",PlayerInfo[playerid][pWeapon7]);
    INI_Int("Weapon8",PlayerInfo[playerid][pWeapon8]);
    INI_Int("Weapon9",PlayerInfo[playerid][pWeapon9]);
    INI_Int("Weapon10",PlayerInfo[playerid][pWeapon10]);
    INI_Int("Weapon11",PlayerInfo[playerid][pWeapon11]);
    INI_Int("Weapon12",PlayerInfo[playerid][pWeapon12]);
    INI_Int("Weapon13",PlayerInfo[playerid][pWeapon13]);
    INI_Int("Weapon14",PlayerInfo[playerid][pWeapon14]);
    INI_Int("Ammo1",PlayerInfo[playerid][pAmmo1]);
    INI_Int("Ammo2",PlayerInfo[playerid][pAmmo2]);
    INI_Int("Ammo3",PlayerInfo[playerid][pAmmo3]);
    INI_Int("Ammo4",PlayerInfo[playerid][pAmmo4]);
    INI_Int("Ammo5",PlayerInfo[playerid][pAmmo5]);
    INI_Int("Ammo6",PlayerInfo[playerid][pAmmo6]);
    INI_Int("Ammo7",PlayerInfo[playerid][pAmmo7]);
    INI_Int("Ammo8",PlayerInfo[playerid][pAmmo8]);
    INI_Int("Ammo9",PlayerInfo[playerid][pAmmo9]);
    INI_Int("Ammo10",PlayerInfo[playerid][pAmmo10]);
    INI_Int("Ammo11",PlayerInfo[playerid][pAmmo11]);
    INI_Int("Ammo12",PlayerInfo[playerid][pAmmo12]);
    INI_Int("Ammo13",PlayerInfo[playerid][pAmmo13]);
    INI_Int("Ammo14",PlayerInfo[playerid][pAmmo14]);
    INI_Float("Health", PlayerInfo[playerid][pHealth]);
	INI_Int("BusinessMoney",PlayerInfo[playerid][BusinessMoney]);
	INI_Int("DriverLicense",PlayerInfo[playerid][pDriverLicense]);
	INI_Int("Age",PlayerInfo[playerid][pAge]);
	INI_Int("Gender",PlayerInfo[playerid][pGender]);
	INI_Int("InJail",PlayerInfo[playerid][pInJail]);
	INI_Int("InJailTime",PlayerInfo[playerid][pInJailTime]);
	INI_Int("Mask",PlayerInfo[playerid][pMask]);
	INI_Int("FightingStyle",PlayerInfo[playerid][pFightingStyle]);
	INI_Int("Boombox",PlayerInfo[playerid][pBoombox]);
	INI_Float("XPos",PlayerInfo[playerid][pXPos]);
	INI_Float("YPos",PlayerInfo[playerid][pYPos]);
	INI_Float("ZPos",PlayerInfo[playerid][pZPos]);
	INI_Int("Interior",PlayerInfo[playerid][pInterior]);
	INI_Int("VirtualWorld",PlayerInfo[playerid][pVirtualWorld]);
	INI_Int("Banned", PlayerInfo[playerid][pBanned]);
	INI_Int("Experience", PlayerInfo[playerid][pExperience]);
	INI_Int("Seeds", PlayerInfo[playerid][dSeeds]);
	INI_Int("Water", PlayerInfo[playerid][dWater]);
    return 1;
}

forward LoadIP_data(playerid, name[], value[]);
public LoadIP_data(playerid, name[], value[])
{
    INI_String("Ip", PlayerInfo[ playerid ][ BannedIP ], 33);
    return 1;
}

forward loadbiz_data(idx, name[], value[]);
public loadbiz_data(idx, name[], value[])
{
    INI_Int("bOwned", BusinessInfo[idx][bOwned]);
    INI_Int("bPrice", BusinessInfo[idx][bPrice]);
    INI_String("bOwner", BusinessInfo[idx][bOwner], 24);
    INI_Int("bType", BusinessInfo[idx][bType]);
    INI_Int("bLocked", BusinessInfo[idx][bLocked]);
    INI_Int("bMoney", BusinessInfo[idx][bMoney]);
    INI_Float("bEntranceX", BusinessInfo[idx][bEntranceX]);
    INI_Float("bEntranceY", BusinessInfo[idx][bEntranceY]);
    INI_Float("bEntranceZ", BusinessInfo[idx][bEntranceZ]);
    INI_Float("bEntranceA", BusinessInfo[idx][bEntranceA]);
    INI_Float("bExitX", BusinessInfo[idx][bExitX]);
    INI_Float("bExitY", BusinessInfo[idx][bExitY]);
    INI_Float("bExitZ", BusinessInfo[idx][bExitZ]);
    INI_Float("bExitA", BusinessInfo[idx][bExitA]);
    INI_Int("bInt", BusinessInfo[idx][bInt]);
    INI_Int("bWorld", BusinessInfo[idx][bWorld]);
    INI_Int("bInsideInt", BusinessInfo[idx][bInsideInt]);
    INI_Int("bInsideWorld", BusinessInfo[idx][bInsideWorld]);
    INI_String("bName", BusinessInfo[idx][bName], 128);
    return 1;
}

forward loadhouse_data(idx, name[], value[]);
public loadhouse_data(idx, name[], value[])
{
    INI_Int("hOwned", HouseInfo[idx][hOwned]);
    INI_Int("hPrice", HouseInfo[idx][hPrice]);
    INI_String("hOwner", HouseInfo[idx][hOwner], 24);
    INI_Int("hLocked", HouseInfo[idx][hLocked]);
    INI_Int("hMoney", HouseInfo[idx][hMoney]);
    INI_Float("hEntranceX", HouseInfo[idx][hEntranceX]);
    INI_Float("hEntranceY", HouseInfo[idx][hEntranceY]);
    INI_Float("hEntranceZ", HouseInfo[idx][hEntranceZ]);
    INI_Float("hEntranceA", HouseInfo[idx][hEntranceA]);
    INI_Float("hExitX", HouseInfo[idx][hExitX]);
    INI_Float("hExitY", HouseInfo[idx][hExitY]);
    INI_Float("hExitZ", HouseInfo[idx][hExitZ]);
    INI_Float("hExitA", HouseInfo[idx][hExitA]);
    INI_Int("hInt", HouseInfo[idx][hInt]);
    INI_Int("hWorld", HouseInfo[idx][hWorld]);
    INI_Int("hInsideInt", HouseInfo[idx][hInsideInt]);
    INI_Int("hInsideWorld", HouseInfo[idx][hInsideWorld]);
    return 1;
}

main()
{
	print("Illusionial Roleplay");
	print("scripted by chrillzen");
	print("-");
}


forward UnJail(playerid);
forward ProxDetector(Float:radi, playerid, string[],col1,col2,col3,col4,col5);
forward PlayerActionMessage(playerid,Float:radius,message[]);
forward PoliceBroadcast(color,const string[],level);
forward ABroadCast(color,const string[],level);
forward GiveRespectAgain(playerid);
forward Payday(playerid);

/*

	Variables
	
*/

new bool:isAlive[MAX_PLAYERS];
new bool:stopanimAllowed[MAX_PLAYERS];
new bool:rentingVehicle[MAX_PLAYERS];
new DMVcar[5];
new rentCAR[5];
new Pickup[10];
new playerRace[MAX_PLAYERS];
new Text:txtTimeDisp;
new hour, minute;
new timestr[32];
new Text3D:DamageLabel[8];
new Float:Deadx[MAX_PLAYERS], Float:Deady[MAX_PLAYERS], Float:Deadz[MAX_PLAYERS];
new DMVcp[MAX_PLAYERS];
new BigEar[MAX_PLAYERS];
new gMuted[MAX_PLAYERS];
new Duty[MAX_PLAYERS];
new aDuty[MAX_PLAYERS];
new PlayerNeedsHelp[MAX_PLAYERS];
new Warns[MAX_PLAYERS];
new Respect[MAX_PLAYERS];
new vCar[MAX_PLAYERS];
new IsSmokingJoint[MAX_PLAYERS];
new IsSmokingCigarette[MAX_PLAYERS];
new IsDrinkingBeer[MAX_PLAYERS];
new IsCocaineHigh[MAX_PLAYERS];
new IsLSDHigh[MAX_PLAYERS];
new BackOut[MAX_PLAYERS];
new gTeam[MAX_PLAYERS];
new oncall[MAX_PLAYERS];
new animation[200];
new Mobile[MAX_PLAYERS];
new iscalled[MAX_PLAYERS];
new onoff[MAX_PLAYERS] = 1;
new Spray[MAX_PLAYERS];
new Cash[MAX_PLAYERS];
new Text:ServerTimeTXT;
new ServerTime = 12;
new bool:OOCenable = true;
new Dice[MAX_PLAYERS];
new bool:greetInvited[MAX_PLAYERS];
new greetNumber[MAX_PLAYERS];
new gPlayerUsingLoopingAnim[MAX_PLAYERS];
new Player_Greet[MAX_PLAYERS];
new gPlayerLoggin[MAX_PLAYERS char];
new Previous_Colour[ MAX_PLAYERS ];
new InsideBiz[MAX_PLAYERS];
new InsideHouse[MAX_PLAYERS];
new MaskOn[MAX_PLAYERS];
new Text3D:NameTag[MAX_PLAYERS];
new AdvertiseAllowed[MAX_PLAYERS];
new CP[MAX_PLAYERS];
new fine_weather_ids[] = {1,2,3,4,5,6,7,12,13,14,15,17,18,24,25,26,27,28,29,30,40};
new foggy_weather_ids[] = {9,19,20,31,32};
new wet_weather_ids[] = {8};
new masknumber[MAX_PLAYERS];
new hit[MAX_PLAYERS];
new bool:TakingDriverLicense[MAX_PLAYERS];
new engine, lights, alarm, doors, bonnet, boot, objective;
new door0, door1, door2, door3;
new cell0, cell1, cell2, cell3, cell4, cell5, cell6, cell7;
new Text:Textdraw0;
new Text:Textdraw1;
new Text:Textdraw2;
new Text:Textdraw3;
new Text:Textdraw4;
new Text:Textdraw5;
new Text:Textdraw6;
new Text:Textdraw7;
new Text:Textdraw8;
new Text:Textdraw9;
new Text:Textdraw10;
new Text:Textdraw11;
new Text:Textdraw12;
new Text:Textdraw13;
new Text:Textdraw14;
new Text:Textdraw15;
new Text:Textdraw16;
new Text:Textdraw17;
new Text:Textdraw18;
new String[128], Float:SpecX[MAX_PLAYERS], Float:SpecY[MAX_PLAYERS], Float:SpecZ[MAX_PLAYERS], vWorld[MAX_PLAYERS], Inter[MAX_PLAYERS];
new IsSpecing[MAX_PLAYERS], Name[MAX_PLAYER_NAME], IsBeingSpeced[MAX_PLAYERS],spectatorid[MAX_PLAYERS];

/* Gamemodeinit */

public OnGameModeInit()
{
	//rash
	mysql_connect(SQL_HOST, SQL_USER, SQL_DB, SQL_PASS);
	if(mysql_ping() == 1)
    {
        mysql_debug(1);
        printf("[MYSQL]: подключение успешно", SQL_DB);
    }
	else printf("[MYSQL]: [ERROR]: не удалось подключиться к бд", SQL_DB);
	//rash
	SetGameModeText("I:RP 0.7");
	DisableInteriorEnterExits();
	SetNameTagDrawDistance(10.0);
	SetTimer("MoneyTimer", 1000, 1);
	SetTimer("HideTimer", 3000, true);
 	ManualVehicleEngineAndLights();
 	FadeInit();
 	
 	txtTimeDisp = TextDrawCreate(605.0,25.0,"00:00");
	TextDrawUseBox(txtTimeDisp, 0);
	TextDrawFont(txtTimeDisp, 3);
	TextDrawSetShadow(txtTimeDisp,0); // no shadow
    TextDrawSetOutline(txtTimeDisp,2); // thickness 1
    TextDrawBackgroundColor(txtTimeDisp,0x000000FF);
    TextDrawColor(txtTimeDisp,0xFFFFFFFF);
    TextDrawAlignment(txtTimeDisp,3);
	TextDrawLetterSize(txtTimeDisp,0.5,1.5);
	
	LoadVehicles();
	LoadDealerships();
	LoadFuelStations();

	/*SpeedoBox = TextDrawCreate(345.000, 363.000, "~n~~n~~n~~n~");
	TextDrawAlignment(SpeedoBox, 2);
	TextDrawLetterSize(SpeedoBox, 0.500, 1.400);
	TextDrawUseBox(SpeedoBox, 1);
	TextDrawBoxColor(SpeedoBox, 153);
	TextDrawTextSize(SpeedoBox, 0.000, 340.000);*/

	for(new i=0; i < MAX_PLAYERS; i++)
	{
		if(IsPlayerConnected(i))
		{
			OnPlayerConnect(i);
		}
	}
	for(new i=1; i < MAX_DVEHICLES; i++)
	{
		UpdateVehicle(i, 0);
	}
	for(new i=1; i < MAX_DEALERSHIPS; i++)
	{
		UpdateDealership(i, 0);
	}
	for(new i=1; i < MAX_FUEL_STATIONS; i++)
	{
		UpdateFuelStation(i, 0);
	}

	maintimer = SetTimer("MainTimer", 1000, true);
	speedotimer = SetTimer("Speedometer", 555, true);
	savetimer = SetTimer("SaveTimer", 2222, true);

	UpdateTimeAndWeather();
	SetTimer("UpdateTimeAndWeather",1000 * 60,1);
	
	AddPlayerClass(26,2178.3579,-1770.3918,13.5453,359.5355,0,0,0,0,0,0); // Civilian Spawn
	
  	for(new j = 0; j < MAX_PLAYERS; j++)
    {
        SetTimerEx("Payday",1*60*60*1000,true,"i",j);
    }
	
	Textdraw0 = TextDrawCreate(650.000000, 80.000000, "asd");
	TextDrawBackgroundColor(Textdraw0, 255);
	TextDrawFont(Textdraw0, 1);
	TextDrawLetterSize(Textdraw0, 0.800000, -16.000000);
	TextDrawColor(Textdraw0, -1);
	TextDrawSetOutline(Textdraw0, 0);
	TextDrawSetProportional(Textdraw0, 1);
	TextDrawSetShadow(Textdraw0, 1);
	TextDrawUseBox(Textdraw0, 1);
	TextDrawBoxColor(Textdraw0, 255);
	TextDrawTextSize(Textdraw0, -50.000000, 0.000000);

	Textdraw1 = TextDrawCreate(650.000000, 524.000000, "asd");
	TextDrawBackgroundColor(Textdraw1, 255);
	TextDrawFont(Textdraw1, 1);
	TextDrawLetterSize(Textdraw1, 0.800000, -16.000000);
	TextDrawColor(Textdraw1, -1);
	TextDrawSetOutline(Textdraw1, 0);
	TextDrawSetProportional(Textdraw1, 1);
	TextDrawSetShadow(Textdraw1, 1);
	TextDrawUseBox(Textdraw1, 1);
	TextDrawBoxColor(Textdraw1, 255);
	TextDrawTextSize(Textdraw1, -50.000000, 0.000000);

	Textdraw2 = TextDrawCreate(6.000000, 391.000000, "Welcome to Los Angeles, the city of angels. This is where you'll be staying.");
	TextDrawBackgroundColor(Textdraw2, 255);
	TextDrawFont(Textdraw2, 1);
	TextDrawLetterSize(Textdraw2, 0.500000, 1.000000);
	TextDrawColor(Textdraw2, -1);
	TextDrawSetOutline(Textdraw2, 0);
	TextDrawSetProportional(Textdraw2, 1);
	TextDrawSetShadow(Textdraw2, 1);

	Textdraw3 = TextDrawCreate(5.000000, 405.000000, "This is your chance to find new friends, make money and maybe seek fame?");
	TextDrawBackgroundColor(Textdraw3, 255);
	TextDrawFont(Textdraw3, 1);
	TextDrawLetterSize(Textdraw3, 0.500000, 1.000000);
	TextDrawColor(Textdraw3, -1);
	TextDrawSetOutline(Textdraw3, 0);
	TextDrawSetProportional(Textdraw3, 1);
	TextDrawSetShadow(Textdraw3, 1);

	Textdraw4 = TextDrawCreate(6.000000, 419.000000, "Whatever you are looking for, you can find here. In the city of angels.");
	TextDrawBackgroundColor(Textdraw4, 255);
	TextDrawFont(Textdraw4, 1);
	TextDrawLetterSize(Textdraw4, 0.500000, 1.000000);
	TextDrawColor(Textdraw4, -1);
	TextDrawSetOutline(Textdraw4, 0);
	TextDrawSetProportional(Textdraw4, 1);
	TextDrawSetShadow(Textdraw4, 1);
	
	Textdraw9 = TextDrawCreate(6.000000, 391.000000, "If you look around you can find different banks in Los Angeles.");
	TextDrawBackgroundColor(Textdraw9, 255);
	TextDrawFont(Textdraw9, 1);
	TextDrawLetterSize(Textdraw9, 0.500000, 1.000000);
	TextDrawColor(Textdraw9, -1);
	TextDrawSetOutline(Textdraw9, 0);
	TextDrawSetProportional(Textdraw9, 1);
	TextDrawSetShadow(Textdraw9, 1);

	Textdraw10 = TextDrawCreate(5.000000, 405.000000, "We've already set up a bank account for you so you can use the bank.");
	TextDrawBackgroundColor(Textdraw10, 255);
	TextDrawFont(Textdraw10, 1);
	TextDrawLetterSize(Textdraw10, 0.500000, 1.000000);
	TextDrawColor(Textdraw10, -1);
	TextDrawSetOutline(Textdraw10, 0);
	TextDrawSetProportional(Textdraw10, 1);
	TextDrawSetShadow(Textdraw10, 1);

	Textdraw11 = TextDrawCreate(6.000000, 419.000000, "You will also find various ATM's that are located around Los Angeles.");
	TextDrawBackgroundColor(Textdraw11, 255);
	TextDrawFont(Textdraw11, 1);
	TextDrawLetterSize(Textdraw11, 0.500000, 1.000000);
	TextDrawColor(Textdraw11, -1);
	TextDrawSetOutline(Textdraw11, 0);
	TextDrawSetProportional(Textdraw11, 1);
	TextDrawSetShadow(Textdraw11, 1);
	
	Textdraw5 = TextDrawCreate(6.000000, 391.000000, "Los Angeles is not an innocent city. It's filled with illegal organizations.");
	TextDrawBackgroundColor(Textdraw5, 255);
	TextDrawFont(Textdraw5, 1);
	TextDrawLetterSize(Textdraw5, 0.500000, 1.000000);
	TextDrawColor(Textdraw5, -1);
	TextDrawSetOutline(Textdraw5, 0);
	TextDrawSetProportional(Textdraw5, 1);
	TextDrawSetShadow(Textdraw5, 1);
	
	Textdraw12 = TextDrawCreate(5.000000, 405.000000, "If you feel like working as a postman doesn't pay you enough, maybe");
	TextDrawBackgroundColor(Textdraw12, 255);
	TextDrawFont(Textdraw12, 1);
	TextDrawLetterSize(Textdraw12, 0.500000, 1.000000);
	TextDrawColor(Textdraw12, -1);
	TextDrawSetOutline(Textdraw12, 0);
	TextDrawSetProportional(Textdraw12, 1);
	TextDrawSetShadow(Textdraw12, 1);
	
	Textdraw13 = TextDrawCreate(6.000000, 419.000000, "you should consider taking contact with one of the associates.");
	TextDrawBackgroundColor(Textdraw13, 255);
	TextDrawFont(Textdraw13, 1);
	TextDrawLetterSize(Textdraw13, 0.500000, 1.000000);
	TextDrawColor(Textdraw13, -1);
	TextDrawSetOutline(Textdraw13, 0);
	TextDrawSetProportional(Textdraw13, 1);
	TextDrawSetShadow(Textdraw13, 1);
	
	Textdraw6 = TextDrawCreate(6.000000, 391.000000, "This is not just the city of angels, but also the city of broken souls.");
	TextDrawBackgroundColor(Textdraw6, 255);
	TextDrawFont(Textdraw6, 1);
	TextDrawLetterSize(Textdraw6, 0.500000, 1.000000);
	TextDrawColor(Textdraw6, -1);
	TextDrawSetOutline(Textdraw6, 0);
	TextDrawSetProportional(Textdraw6, 1);
	TextDrawSetShadow(Textdraw6, 1);
	
	Textdraw14 = TextDrawCreate(5.000000, 405.000000, "Out on the cold streets of L.A, people fall for drugs everyday.");
	TextDrawBackgroundColor(Textdraw14, 255);
	TextDrawFont(Textdraw14, 1);
	TextDrawLetterSize(Textdraw14, 0.500000, 1.000000);
	TextDrawColor(Textdraw14, -1);
	TextDrawSetOutline(Textdraw14, 0);
	TextDrawSetProportional(Textdraw14, 1);
	TextDrawSetShadow(Textdraw14, 1);
	
	Textdraw15 = TextDrawCreate(6.000000, 419.000000, "Will you become a victim of the drug or the one that hands it out?");
	TextDrawBackgroundColor(Textdraw15, 255);
	TextDrawFont(Textdraw15, 1);
	TextDrawLetterSize(Textdraw15, 0.500000, 1.000000);
	TextDrawColor(Textdraw15, -1);
	TextDrawSetOutline(Textdraw15, 0);
	TextDrawSetProportional(Textdraw15, 1);
	TextDrawSetShadow(Textdraw15, 1);
	
	Textdraw7 = TextDrawCreate(6.000000, 391.000000, "Just be careful, because you don't want to get caught by the police.");
	TextDrawBackgroundColor(Textdraw7, 255);
	TextDrawFont(Textdraw7, 1);
	TextDrawLetterSize(Textdraw7, 0.500000, 1.000000);
	TextDrawColor(Textdraw7, -1);
	TextDrawSetOutline(Textdraw7, 0);
	TextDrawSetProportional(Textdraw7, 1);
	TextDrawSetShadow(Textdraw7, 1);
	
	Textdraw16 = TextDrawCreate(5.000000, 405.000000, "You will find the Los Angeles Police patrol the streets 24/7.");
	TextDrawBackgroundColor(Textdraw16, 255);
	TextDrawFont(Textdraw16, 1);
	TextDrawLetterSize(Textdraw16, 0.500000, 1.000000);
	TextDrawColor(Textdraw16, -1);
	TextDrawSetOutline(Textdraw16, 0);
	TextDrawSetProportional(Textdraw16, 1);
	TextDrawSetShadow(Textdraw16, 1);
	
	Textdraw8 = TextDrawCreate(6.000000, 391.000000, "If you feel like getting a job then you should look for this building.");
	TextDrawBackgroundColor(Textdraw8, 255);
	TextDrawFont(Textdraw8, 1);
	TextDrawLetterSize(Textdraw8, 0.500000, 1.000000);
	TextDrawColor(Textdraw8, -1);
	TextDrawSetOutline(Textdraw8, 0);
	TextDrawSetProportional(Textdraw8, 1);
	TextDrawSetShadow(Textdraw8, 1);
	
	Textdraw17 = TextDrawCreate(5.000000, 405.000000, "This is Los Angeles's city hall, also home to the L.A court.");
	TextDrawBackgroundColor(Textdraw17, 255);
	TextDrawFont(Textdraw17, 1);
	TextDrawLetterSize(Textdraw17, 0.500000, 1.000000);
	TextDrawColor(Textdraw17, -1);
	TextDrawSetOutline(Textdraw17, 0);
	TextDrawSetProportional(Textdraw17, 1);
	TextDrawSetShadow(Textdraw17, 1);
	
	Textdraw18 = TextDrawCreate(6.000000, 419.000000, "This is the end of this introduction, we hope you enjoy your stay.");
	TextDrawBackgroundColor(Textdraw18, 255);
	TextDrawFont(Textdraw18, 1);
	TextDrawLetterSize(Textdraw18, 0.500000, 1.000000);
	TextDrawColor(Textdraw18, -1);
	TextDrawSetOutline(Textdraw18, 0);
	TextDrawSetProportional(Textdraw18, 1);
	TextDrawSetShadow(Textdraw18, 1);

	DMVcar[0] = AddStaticVehicle(405,2052.5676,-1903.7029,13.4219,180.1635,1,1);
	DMVcar[1] = AddStaticVehicle(405,2055.8943,-1904.0417,13.4219,180.6969,1,1);
	DMVcar[2] = AddStaticVehicle(405,2059.0757,-1903.9192,13.4219,180.6096,1,1);
	DMVcar[3] = AddStaticVehicle(405,2062.2998,-1903.7009,13.4218,180.0933,1,1);
	DMVcar[4] = AddStaticVehicle(405,2065.5630,-1904.1188,13.4219,179.6829,1,1);
	
	rentCAR[0] = AddStaticVehicle(527,1844.4408,-1871.2946,13.1034,0.4020,0,0);
	rentCAR[1] = AddStaticVehicle(527,1841.2330,-1871.4095,13.1051,0.7591,0,0);
	rentCAR[2] = AddStaticVehicle(527,1838.0530,-1871.3665,13.1053,0.4366,0,0);
	rentCAR[3] = AddStaticVehicle(527,1834.8795,-1871.4850,13.1035,0.8579,0,0);
	rentCAR[4] = AddStaticVehicle(527,1802.3534,-1866.9581,13.2909,0.2767,0,0);

	
	Pickup[0] = CreatePickup(1239, 1, 2045.0376,-1913.1846,13.5469, -1);
	Pickup[1] = CreatePickup(1239, 1, 1684.4441,-1343.2681,17.4371, -1);
	Pickup[2] = CreatePickup(1239, 1, 2316.6206,-15.2233,26.7422, -1);
	Pickup[3] = CreatePickup(1239, 1, 772.2167,5.2337,1000.7802, -1);
	Pickup[4] = CreatePickup(1239, 1, 759.2585,-59.2561,1000.7802, -1);
	Pickup[5] = CreatePickup(1274, 1, -23.5424,-55.6289,1003.5469, -1);
	Pickup[6] = CreatePickup(1274, 1, -31.0680,-29.0295,1003.5573, -1);
	Pickup[7] = CreatePickup(1274, 1, -22.2473,-138.6266,1003.5469, -1);
	Pickup[8] = CreatePickup(1274, 1, -28.2207,-89.9549,1003.5469, -1);
	Pickup[9] = CreatePickup(1239, 1, -2237.1465,130.1773,1035.4141, -1);

	
	new string[256];
 	new biztext[128];
 	
    for(new idx = 1; idx < sizeof(BusinessInfo); idx++)
    {
	    format(string, sizeof(string), BPATH, idx);//formats the file path, with the biz ID
	    INI_ParseFile(string, "loadbiz_%s", .bExtra = true, .extra = idx );//This is very hard to explain, but it basically loads the info from the file(More in Y_Less y_ini tutorial.)
	    BusinessInfo[idx][bOutsideIcon] = CreateDynamicPickup(1239, 1, BusinessInfo[idx][bEntranceX], BusinessInfo[idx][bEntranceY], BusinessInfo[idx][bEntranceZ], BusinessInfo[idx][bWorld]); //Creates a pickup at the business entrance.

	   	switch(BusinessInfo[idx][bType])
	    {
	 			case 20: biztext = "Dealership";
	 			case 19: biztext = "Electronic Store";
	   			case 18: biztext = "Ammunition";
	   			case 17: biztext = "Gym";
	   			case 16: biztext = "Hotel";
	   			case 15: biztext = "Motel";
	   			case 14: biztext = "Diner";
	         	case 13: biztext = "Tattoo Store";
	         	case 12: biztext = "Barbershop";
	            case 11: biztext = "Flower Store";
	           	case 10: biztext = "98 Cents";
	    		case 9: biztext = "69 Cents";
	            case 8: biztext = "Liqour Store";
		    	case 7: biztext = "Restaurant";
		    	case 6: biztext = "Bank";
		    	case 5: biztext = "Hospital";
		        case 4: biztext = "Police Station";
		        case 3: biztext = "24/7";
		        case 2: biztext = "Club";
		        case 1: biztext = "Bar";
		        case 0: biztext = "Clothes Shop";
	    }
	    if(BusinessInfo[idx][bOwned] == 0)
	    {
	        format(string,sizeof(string),""COL_BROWN"Owner: "COL_WHITE"None\n"COL_BROWN"Price: "COL_WHITE"$%d\n"COL_BROWN"Type: "COL_WHITE"%s\n"COL_BROWN"Street Number: "COL_WHITE"%d", BusinessInfo[idx][bPrice], biztext, idx);
	        BusinessInfo[idx][DLabel] = Create3DTextLabel(string, 0xFFFFFF, BusinessInfo[idx][bEntranceX],BusinessInfo[idx][bEntranceY],BusinessInfo[idx][bEntranceZ], 10.0, 0, 0);
	    }
	    else if(BusinessInfo[idx][bOwned] == 1)
	    {
	        format(string,sizeof(string),""COL_BROWN"Owner: "COL_WHITE"%s\n"COL_BROWN"Name: "COL_WHITE"%s\n"COL_BROWN"Type: "COL_WHITE"%s\n"COL_BROWN"Street Number: "COL_WHITE"%d", BusinessInfo[idx][bOwner], BusinessInfo[idx][bName], biztext, idx);
	        BusinessInfo[idx][DLabel] = Create3DTextLabel(string, 0xFFFFFF,  BusinessInfo[idx][bEntranceX],BusinessInfo[idx][bEntranceY], BusinessInfo[idx][bEntranceZ], 10.0, 0, 0);
	    }
	}
	
	for(new idz = 1; idz < sizeof(HouseInfo); idz++)
    {
	    format(string, sizeof(string), HPATH, idz);
	    INI_ParseFile(string, "loadhouse_%s", .bExtra = true, .extra = idz );

	    if(HouseInfo[idz][hOwned] == 0)
	    {
	        format(string,sizeof(string),""COL_BROWN"Owner: "COL_WHITE"None\n"COL_BROWN"Price: "COL_WHITE"$%d\n"COL_BROWN"Street Number: "COL_WHITE"%d", HouseInfo[idz][hPrice], idz);
	        HouseInfo[idz][hDLabel] = Create3DTextLabel(string, 0xFFFFFF, HouseInfo[idz][hEntranceX],HouseInfo[idz][hEntranceY],HouseInfo[idz][hEntranceZ], 10.0, 0, 0);
    	    HouseInfo[idz][hOutsideIcon] = CreateDynamicPickup(1273, 1, HouseInfo[idz][hEntranceX], HouseInfo[idz][hEntranceY], HouseInfo[idz][hEntranceZ], HouseInfo[idz][hWorld]);
	    }
     	else if(HouseInfo[idz][hOwned] == 1)
	    {
	        format(string,sizeof(string),""COL_BROWN"Owner: "COL_WHITE"%s\n"COL_BROWN"Street Number: "COL_WHITE"%d", HouseInfo[idz][hOwner], idz);
	        HouseInfo[idz][hDLabel] = Create3DTextLabel(string, 0xFFFFFF,  HouseInfo[idz][hEntranceX],HouseInfo[idz][hEntranceY], HouseInfo[idz][hEntranceZ], 10.0, 0, 0);
    	    HouseInfo[idz][hOutsideIcon] = CreateDynamicPickup(1272, 1, HouseInfo[idz][hEntranceX], HouseInfo[idz][hEntranceY], HouseInfo[idz][hEntranceZ], HouseInfo[idz][hWorld]);
	    }
	}

	// Ganton & Bloods
	CreateDynamicObject(851,2801.6000977,-2033.6999512,12.8999996,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(852,2799.0000000,-2033.9000244,12.6000004,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(926,2797.6999512,-2034.6999512,12.8000002,0.0000000,0.0000000,22.0000000); //
	CreateDynamicObject(2840,2797.3000488,-2034.3000488,12.6000004,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1439,2802.5000000,-2031.0999756,12.6000004,0.0000000,0.0000000,270.0000000); //
	CreateDynamicObject(1415,2802.3000488,-2029.3000488,12.6000004,0.0000000,0.0000000,270.0000000); //
	CreateDynamicObject(1362,2796.0000000,-2034.6999512,13.1999998,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1712,2756.0000000,-2016.9000244,12.6000004,0.0000000,0.0000000,60.0000000); //
	CreateDynamicObject(1712,2759.6000977,-2017.4000244,12.6000004,0.0000000,0.0000000,230.0000000); //
	CreateDynamicObject(2311,2757.3999023,-2017.9000244,12.6000004,0.0000000,0.0000000,64.0000000); //
	CreateDynamicObject(1481,2760.0000000,-2014.4000244,13.3000002,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1485,2757.6000977,-2016.6999512,13.1000004,0.0000000,0.0000000,20.0000000); //
	CreateDynamicObject(1509,2757.6000977,-2016.8000488,13.3000002,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(2103,2757.3994141,-2017.7998047,13.1000004,0.0000000,0.0000000,119.9981689); //
	CreateDynamicObject(2058,2758.0000000,-2016.5000000,13.1000004,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(2857,2758.1999512,-2014.6999512,12.6000004,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(2840,2757.8000488,-2017.3000488,13.1000004,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(2908,2801.8999023,-2030.5999756,13.3999996,0.0000000,0.0000000,80.0000000); //
	CreateDynamicObject(2906,2801.8000488,-2031.5999756,13.3999996,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1369,2763.6000977,-2013.0000000,13.1999998,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(3414,2732.8999023,-2065.3999023,14.3999996,0.0000000,0.0000000,180.0000000); //
	CreateDynamicObject(18451,2749.6000977,-2074.1999512,12.1999998,0.0000000,0.0000000,120.0000000); //
	CreateDynamicObject(2971,2727.6000977,-2066.8000488,12.3000002,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1441,2727.6000977,-2060.1000977,13.1000004,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(2370,2733.3000488,-2065.3999023,12.3000002,0.0000000,0.0000000,20.0000000); //
	CreateDynamicObject(1810,2732.1999512,-2064.8999023,12.3000002,0.0000000,0.0000000,40.0000000); //
	CreateDynamicObject(1486,2732.8000488,-2064.8000488,13.3000002,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(2044,2733.0000000,-2065.0000000,13.1999998,0.0000000,0.0000000,240.0000000); //
	CreateDynamicObject(853,2731.8999023,-2061.0000000,12.6999998,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1358,2745.1999512,-2075.3000488,13.0000000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(4227,2744.0000000,-2014.0000000,14.1000004,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1650,2751.5000000,-1949.0999756,16.6000004,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(2315,2744.1000977,-1943.5000000,16.2999992,0.0000000,0.0000000,30.0000000); //
	CreateDynamicObject(1712,2743.8000488,-1941.0000000,16.2999992,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1712,2745.3000488,-1945.4000244,16.2999992,0.0000000,0.0000000,180.0000000); //
	CreateDynamicObject(2894,2744.1999512,-1943.4000244,16.7999992,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1544,2743.8000488,-1943.4000244,16.7999992,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(2055,2747.3000488,-1939.8000488,18.8999996,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(2056,2748.0000000,-1939.8000488,18.3999996,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(2051,2748.5000000,-1939.8000488,18.3999996,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(2049,2749.1000977,-1939.8000488,18.3999996,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(2047,2744.8999023,-1940.5999756,19.2000008,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1421,2794.1000977,-1948.0000000,17.1000004,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(852,2791.8999023,-1947.4000244,16.2999992,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1438,2795.1000977,-1942.3000488,16.2999992,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(2846,2794.6999512,-1944.5999756,16.2999992,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(2845,2795.5000000,-1945.4000244,16.2999992,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(2843,2794.8000488,-1945.6999512,16.2999992,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(15028,2796.5000000,-1946.4000244,16.5000000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1528,2787.3999023,-1962.5999756,13.8999996,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1709,2781.6999512,-2033.3000488,12.6000004,0.0000000,0.0000000,180.0000000); //
	CreateDynamicObject(2096,2669.1000977,-1989.6999512,13.0000000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1757,2634.5000000,-1994.4000244,13.0000000,0.0000000,0.0000000,45.0000000); //
	CreateDynamicObject(2103,2634.3000488,-1995.0999756,13.0000000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3594,2656.1999512,-2039.0999756,13.1999998,0.0000000,0.0000000,50.0000000); //
	CreateDynamicObject(2676,2654.1999512,-2034.6999512,12.6999998,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3593,2657.5000000,-2033.6999512,13.3000002,0.0000000,0.0000000,20.0000000); //
	CreateDynamicObject(2674,2654.5000000,-2031.8000488,12.6000004,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(2673,2657.5000000,-2033.3000488,13.1000004,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(852,2655.8000488,-2043.0999756,12.6000004,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1440,2652.0000000,-2045.5999756,13.1000004,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1712,2633.1999512,-2003.0000000,12.6000004,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1421,2478.3999023,-1714.3000488,13.3000002,0.0000000,0.0000000,265.0000000); //
	CreateDynamicObject(2846,2478.1000977,-1713.4000244,12.5000000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(2840,2478.8000488,-1711.9000244,12.5000000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1481,2459.3999023,-1676.1999512,13.1999998,0.0000000,0.0000000,180.0000000); //
	CreateDynamicObject(2102,2461.3000488,-1678.0999756,12.5000000,0.0000000,0.0000000,130.0000000); //
	CreateDynamicObject(1766,2457.6000977,-1677.6999512,12.5000000,0.0000000,0.0000000,210.0000000); //
	CreateDynamicObject(2843,2459.3999023,-1678.8000488,13.3999996,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1433,2456.0000000,-1676.8000488,12.6999998,0.0000000,0.0000000,30.0000000); //
	CreateDynamicObject(1543,2455.8999023,-1677.1999512,13.1999998,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1485,2455.6999512,-1677.3000488,13.1999998,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1509,2456.0000000,-1677.0000000,13.3999996,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1546,2456.1999512,-1677.0999756,13.3000002,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(2814,2456.1000977,-1676.5999756,13.1999998,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1413,2439.1999512,-1678.3000488,14.0000000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1412,2439.1000977,-1673.0000000,13.8999996,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1412,2423.0000000,-1678.3000488,14.0000000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1412,2422.8999023,-1673.0999756,13.8999996,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1412,2436.5000000,-1670.5000000,13.8000002,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1412,2431.1999512,-1670.5000000,13.8000002,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3496,2438.6999512,-1675.6999512,12.6999998,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(3496,2423.3000488,-1675.6999512,12.6999998,0.0000000,0.0000000,270.0000000); //
	CreateDynamicObject(1764,2428.3000488,-1680.5000000,12.8000002,0.0000000,0.0000000,180.0000000); //
	CreateDynamicObject(2311,2429.3999023,-1680.5999756,12.8000002,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1764,2434.1000977,-1680.5000000,12.8000002,0.0000000,0.0000000,180.0000000); //
	CreateDynamicObject(3065,2430.8000488,-1680.8000488,13.3999996,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1544,2429.6000977,-1680.4000244,13.3000002,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(2894,2430.1000977,-1680.5999756,13.3000002,0.0000000,0.0000000,325.0000000); //
	CreateDynamicObject(852,2397.1999512,-1694.1999512,12.6999998,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1747,2398.8999023,-1693.5000000,12.6999998,0.0000000,0.0000000,317.0000000); //
	CreateDynamicObject(1449,2400.1999512,-1693.4000244,13.3000002,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1440,2377.5000000,-1693.9000244,13.1000004,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1439,2382.3999023,-1693.5999756,12.6999998,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1438,2385.0000000,-1694.3000488,12.6000004,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1349,2391.6000977,-1697.4000244,13.1999998,0.0000000,0.0000000,145.0000000); //
	CreateDynamicObject(12957,2415.8000488,-1700.8000488,13.6999998,0.0000000,0.0000000,50.0000000); //
	CreateDynamicObject(2672,2375.1000977,-1696.6999512,12.8999996,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3593,2416.1999512,-1707.8000488,13.5000000,0.0000000,0.0000000,11.0000000); //
	CreateDynamicObject(1525,2419.3000488,-1696.0000000,13.8000002,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1369,2461.8999023,-1689.0999756,13.1000004,0.0000000,0.0000000,120.0000000); //
	CreateDynamicObject(17969,2422.8999023,-1684.1999512,14.1000004,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1292,2439.8999023,-1649.3000488,13.0000000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(2858,2455.8999023,-1680.5000000,13.3000002,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(851,2434.8999023,-1639.1999512,12.8000002,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(850,2425.5000000,-1636.4000244,12.6000004,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(849,2423.6999512,-1644.4000244,12.8000002,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3302,2433.5000000,-1636.0000000,12.5000000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(854,2436.3999023,-1633.4000244,12.6000004,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1344,2424.6000977,-1630.0000000,13.1999998,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(2672,2425.8999023,-1631.3000488,12.6999998,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(2670,2424.1000977,-1631.5000000,12.5000000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(2673,2437.3999023,-1644.0000000,12.8000002,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(2671,2431.6000977,-1641.0000000,12.5000000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(2670,2427.0000000,-1643.8000488,12.6000004,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(2676,2424.0000000,-1640.5000000,12.6000004,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(2672,2438.8999023,-1650.4000244,12.8000002,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(2670,2439.6999512,-1650.0999756,12.6000004,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1349,2434.3000488,-1633.0999756,13.0000000,0.0000000,0.0000000,312.0000000); //
	CreateDynamicObject(1442,2437.6000977,-1636.9000244,13.0000000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(2845,2426.6000977,-1633.0999756,12.3999996,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1438,2467.3999023,-1720.5999756,12.5000000,0.0000000,0.0000000,180.0000000); //
	CreateDynamicObject(1486,2467.6000977,-1720.5999756,13.1999998,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1486,2467.6999512,-1720.8000488,13.1999998,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(2845,2464.8999023,-1720.9000244,12.5000000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(2121,2468.8999023,-1720.3000488,13.0000000,0.0000000,0.0000000,140.0000000); //
	CreateDynamicObject(2121,2467.1999512,-1719.0000000,13.0000000,0.0000000,0.0000000,190.0000000); //
	CreateDynamicObject(1664,2466.8999023,-1721.0000000,13.8000002,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(2820,2465.0000000,-1721.0999756,12.5000000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(2670,2410.5000000,-1696.4000244,12.6999998,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(2676,2410.8000488,-1699.6999512,12.8999996,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3594,2399.6999512,-1742.5000000,13.1999998,0.0000000,0.0000000,320.0000000); //
	CreateDynamicObject(1712,2488.1000977,-1644.9000244,13.1000004,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1509,2490.3999023,-1648.1999512,14.3000002,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1486,2490.3999023,-1645.4000244,13.1999998,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1486,2490.5000000,-1645.0999756,13.1999998,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1512,2490.1999512,-1645.1999512,13.3000002,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(851,2533.1000977,-1664.8000488,14.5000000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(2846,2532.6999512,-1667.3000488,14.1999998,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(2844,2529.3999023,-1669.6999512,14.1999998,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1432,2523.8000488,-1665.0999756,14.1000004,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1544,2523.6000977,-1665.4000244,14.6999998,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1485,2523.8999023,-1664.5999756,14.6999998,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1543,2524.1999512,-1665.3000488,14.6999998,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1481,2524.6999512,-1655.3000488,15.1999998,0.0000000,0.0000000,270.0000000); //
	CreateDynamicObject(1760,2524.5000000,-1660.5000000,14.5000000,0.0000000,0.0000000,270.0000000); //
	CreateDynamicObject(853,2534.1999512,-1701.5999756,12.8000002,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(851,2484.3000488,-1762.6999512,12.8999996,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(849,2485.3999023,-1769.5000000,12.8000002,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(2049,2390.0000000,-1709.0999756,13.6999998,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1528,2228.6999512,-1715.0000000,14.3999996,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1524,2228.6999512,-1715.0000000,15.6999998,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1490,2228.6999512,-1711.0999756,14.6999998,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1531,2486.6999512,-1766.0999756,13.6999998,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1527,2486.6999512,-1767.3000488,13.6000004,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1525,2486.6999512,-1761.8000488,13.6999998,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1526,2486.6999512,-1770.1999512,13.6999998,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1490,2486.6999512,-1762.6999512,13.6999998,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1429,2483.6000977,-1761.8000488,12.8000002,0.0000000,0.0000000,20.0000000); //
	CreateDynamicObject(2677,2484.0000000,-1764.0999756,12.8000002,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(2673,2483.8000488,-1767.8000488,12.6000004,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1764,2381.8000488,-1713.0000000,12.6000004,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1748,2539.6999512,-1705.0000000,12.8999996,0.0000000,0.0000000,320.0000000); //
	CreateDynamicObject(2315,2539.5000000,-1705.0999756,12.3999996,0.0000000,0.0000000,284.0000000); //
	CreateDynamicObject(1712,2538.6000977,-1708.0000000,12.3999996,0.0000000,0.0000000,150.0000000); //
	CreateDynamicObject(2103,2539.8999023,-1706.0999756,12.8999996,0.0000000,0.0000000,300.0000000); //
	CreateDynamicObject(1433,2495.5000000,-1644.0000000,13.0000000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1761,2494.3999023,-1642.5000000,12.8000002,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1544,2495.8000488,-1643.8000488,13.5000000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1751,2495.1999512,-1644.5999756,13.5000000,0.0000000,0.0000000,180.0000000); //

	// Objects converted: 170


	// Locotes

	CreateDynamicObject(947,1981.6877441,-2069.3244629,14.5864763,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(2114,1981.9174805,-2064.1223145,12.5284252,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3819,1986.6296387,-2064.8962402,13.3766098,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(643,1944.2691650,-2060.1450195,13.0173464,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1670,1944.2441406,-2060.1284180,13.4174261,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(14780,1929.1427002,-2066.6171875,13.4136734,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1481,1926.1567383,-2072.5939941,13.2575407,0.0000000,0.0000000,282.0000000); //
	CreateDynamicObject(1717,1921.9816895,-2071.7724609,12.5552511,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1728,1924.0401611,-2073.3264160,12.5565214,0.0000000,0.0000000,160.0000000); //
	CreateDynamicObject(2315,1923.3166504,-2071.2099609,12.5537739,0.0000000,0.0000000,340.0000000); //
	CreateDynamicObject(1829,1802.8098145,-2136.7668457,13.0114040,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(2596,1805.6879883,-2138.7509766,14.8134623,0.0000000,0.0000000,272.0000000); //
	CreateDynamicObject(1728,1801.1010742,-2139.8193359,12.5468750,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1729,1802.6121826,-2140.6677246,12.5468750,0.0000000,0.0000000,218.0000000); //
	CreateDynamicObject(2315,1802.6445312,-2137.8161621,12.5468750,0.0000000,0.0000000,270.0000000); //
	CreateDynamicObject(2768,1802.4212646,-2137.8393555,13.0848227,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(2837,1802.5722656,-2139.2658691,13.0425072,0.0000000,0.0000000,0.0000000); //

	// Objects converted: 17


	//==========================================[Unity Shit]=========================//
	CreateDynamicObject(970,1746.3562012,-1862.1000977,13.1294670,0.0000000,0.0000000,269.7500000); //
	CreateDynamicObject(970,1739.6282959,-1862.0430908,13.1294670,0.0000000,0.0000000,270.2473145); //
	CreateDynamicObject(638,1739.1992188,-1862.6602783,13.2811375,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(638,1739.2028809,-1861.4282227,13.2811375,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(638,1746.7408447,-1861.3875732,13.2811375,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(638,1746.7457275,-1862.8167725,13.2811375,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1215,1746.1964111,-1863.7905273,13.1985693,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1215,1746.1962891,-1863.7900391,13.1985693,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1215,1746.1962891,-1863.7900391,13.1985693,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1215,1739.8013916,-1863.7852783,13.1985693,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1215,1739.8007812,-1863.7851562,13.1985693,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1215,1739.8007812,-1863.7851562,13.1985693,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1215,1739.8007812,-1863.7851562,13.1985693,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1215,1746.1462402,-1863.7907715,13.1985693,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1280,1736.9160156,-1863.5643311,12.9774942,0.0000000,0.0000000,270.5000000); //
	CreateDynamicObject(1280,1749.1251221,-1863.6458740,12.9774942,0.0000000,0.0000000,270.4998779); //
	CreateDynamicObject(970,1826.9801025,-1857.8912354,13.1294670,0.0000000,0.0000000,269.9971924); //
	CreateDynamicObject(970,1826.9676514,-1853.6599121,13.1294670,0.0000000,0.0000000,270.4945068); //
	CreateDynamicObject(970,1826.9545898,-1849.4621582,13.1294670,0.0000000,0.0000000,270.4943848); //
	CreateDynamicObject(970,1826.9375000,-1845.2590332,13.1294670,0.0000000,0.0000000,270.2443848); //
	CreateDynamicObject(970,1826.9466553,-1841.0406494,13.1294670,0.0000000,0.0000000,269.7443848); //
	CreateDynamicObject(970,1826.9487305,-1836.8215332,13.1294670,0.0000000,0.0000000,270.4890137); //
	CreateDynamicObject(970,1826.9372559,-1832.6104736,13.1294670,0.0000000,0.0000000,269.9888916); //
	CreateDynamicObject(970,1829.1540527,-1859.9666748,13.1294670,0.0000000,0.0000000,359.9945068); //
	CreateDynamicObject(638,1827.3437500,-1858.5820312,13.2811375,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(638,1827.3381348,-1855.9531250,13.2811375,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(638,1827.3496094,-1853.2939453,13.2811375,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(638,1827.3518066,-1850.6582031,13.2811375,0.0000000,0.0000000,359.7500000); //
	CreateDynamicObject(638,1827.3660889,-1848.1228027,13.2811375,0.0000000,0.0000000,359.7473145); //
	CreateDynamicObject(638,1827.3742676,-1845.5402832,13.2811375,0.0000000,0.0000000,359.7473145); //
	CreateDynamicObject(638,1827.3652344,-1842.9329834,13.2811375,0.0000000,0.0000000,0.4973145); //
	CreateDynamicObject(638,1827.3521729,-1840.3889160,13.2811375,0.0000000,0.0000000,359.7443848); //
	CreateDynamicObject(638,1827.3634033,-1838.0893555,13.2811375,0.0000000,0.0000000,359.7418213); //
	CreateDynamicObject(638,1827.3679199,-1835.7901611,13.2811375,0.0000000,0.0000000,359.7418213); //
	CreateDynamicObject(638,1827.3741455,-1833.1137695,13.2811375,0.0000000,0.0000000,359.7418213); //
	CreateDynamicObject(638,1827.3797607,-1831.8511963,13.2811375,0.0000000,0.0000000,0.2418213); //
	CreateDynamicObject(638,1828.9910889,-1859.5584717,13.2811375,0.0000000,0.0000000,270.7500000); //
	CreateDynamicObject(638,1829.8489990,-1859.5214844,13.2811375,0.0000000,0.0000000,269.9970703); //
	CreateDynamicObject(638,1828.4588623,-1859.5418701,13.2811375,0.0000000,0.0000000,270.7470703); //
	CreateDynamicObject(1215,1831.5350342,-1859.6440430,13.1424484,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1215,1831.5341797,-1859.6435547,13.1424484,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1215,1831.5341797,-1859.6435547,13.1424484,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1215,1833.3564453,-1845.3035889,13.1424484,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1215,1833.3564453,-1845.3027344,13.1424484,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1215,1833.3564453,-1845.3027344,13.1424484,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1215,1833.3336182,-1840.1114502,13.1424484,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1215,1833.3330078,-1840.1113281,13.1424484,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1215,1833.3330078,-1840.1113281,13.1424484,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1215,1833.3330078,-1840.1113281,13.1424484,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1280,1833.2270508,-1847.5811768,12.9794807,0.0000000,0.0000000,0.5000000); //
	CreateDynamicObject(1280,1833.2496338,-1837.7846680,12.9794807,0.0000000,0.0000000,0.2500000); //

	// Objects converted: 51

	//==========================================[LS Shit]========================//
	CreateDynamicObject(997,1949.9111328,-1781.8007812,12.5468750,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(997,1953.7030029,-1781.6551514,12.5468750,0.0000000,0.0000000,46.0000000); //
	CreateDynamicObject(997,1956.1773682,-1778.9279785,12.5468750,0.0000000,0.0000000,83.7497559); //
	CreateDynamicObject(997,1956.4902344,-1775.3525391,12.5468750,0.0000000,0.0000000,89.9945068); //
	CreateDynamicObject(997,1956.4935303,-1771.6470947,12.5468750,0.0000000,0.0000000,89.9945068); //
	CreateDynamicObject(997,1956.4665527,-1767.9512939,12.5468750,0.0000000,0.0000000,89.9945068); //
	CreateDynamicObject(997,1956.5169678,-1764.2926025,12.5468750,0.0000000,0.0000000,93.9945068); //
	CreateDynamicObject(997,1956.2001953,-1760.7021484,12.5468750,0.0000000,0.0000000,129.7430420); //
	CreateDynamicObject(997,1947.7956543,-1759.5916748,12.5468750,0.0000000,0.0000000,35.4930420); //
	CreateDynamicObject(997,1946.8018799,-1763.2470703,12.5468750,0.0000000,0.0000000,79.7413330); //
	CreateDynamicObject(997,1946.8769531,-1766.8815918,12.5468750,0.0000000,0.0000000,89.7387695); //
	CreateDynamicObject(997,1946.8857422,-1770.4599609,12.5468750,0.0000000,0.0000000,89.7363281); //
	CreateDynamicObject(997,1946.8541260,-1773.9991455,12.5468750,0.0000000,0.0000000,89.7363281); //
	CreateDynamicObject(997,1946.9123535,-1777.6595459,12.5468750,0.0000000,0.0000000,90.7363281); //
	CreateDynamicObject(997,1948.5072021,-1780.8839111,12.5468750,0.0000000,0.0000000,117.7360840); //
	CreateDynamicObject(1215,1948.5533447,-1779.9562988,13.0861988,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1215,1951.3344727,-1781.4013672,13.0861988,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1215,1949.9638672,-1758.5208740,13.0861988,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1215,1954.3642578,-1759.2020264,13.0861988,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1215,1955.9177246,-1762.7939453,13.0861988,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1215,1955.9592285,-1775.9040527,13.0861988,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1215,1955.4746094,-1779.0081787,13.0861988,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1215,1947.3289795,-1776.6534424,13.0861988,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1215,1947.4023438,-1766.2877197,13.0861988,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1215,1947.3792725,-1762.9449463,13.0861988,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1280,1955.9586182,-1764.5498047,12.9482307,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1280,1955.8962402,-1767.8774414,12.9482307,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1280,1955.8834229,-1771.1972656,12.9482307,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1280,1955.8903809,-1774.4010010,12.9482307,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1280,1955.6898193,-1777.4672852,12.9482307,0.0000000,0.0000000,348.0000000); //
	CreateDynamicObject(1280,1955.3179932,-1760.9107666,12.9482307,0.0000000,0.0000000,26.0000000); //
	CreateDynamicObject(1280,1954.0574951,-1780.2668457,12.9482307,0.0000000,0.0000000,309.9991455); //
	CreateDynamicObject(1280,1947.9371338,-1778.2789307,12.9482307,0.0000000,0.0000000,197.9957275); //
	CreateDynamicObject(1280,1947.3907471,-1774.9621582,12.9482307,0.0000000,0.0000000,181.7456207); //
	CreateDynamicObject(1280,1947.3646240,-1771.6065674,12.9482307,0.0000000,0.0000000,180.4913330); //
	CreateDynamicObject(1280,1947.3880615,-1768.1091309,12.9482307,0.0000000,0.0000000,180.4888916); //
	CreateDynamicObject(1280,1947.4639893,-1764.5612793,12.9482307,0.0000000,0.0000000,180.4888916); //
	CreateDynamicObject(1280,1947.8638916,-1760.7520752,12.9482307,0.0000000,0.0000000,162.4888916); //
	CreateDynamicObject(642,1951.7177734,-1767.5971680,13.9701042,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(642,1951.7043457,-1773.9385986,13.9701042,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1257,1968.1098633,-1768.1069336,13.8260670,0.0000000,0.0000000,0.2500000); //
	CreateDynamicObject(910,2170.9533691,-1786.5306396,13.7901602,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(852,2168.1967773,-1787.5806885,12.5203228,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(850,2167.8835449,-1788.3780518,12.6310472,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1238,2157.2038574,-1744.8366699,12.8650551,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1238,2158.4492188,-1746.9569092,12.8650551,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1238,2157.3278809,-1748.7585449,12.6900578,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1238,2155.4790039,-1750.1027832,12.6900578,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1238,2152.5947266,-1750.2028809,12.7150574,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1238,2155.2927246,-1743.6059570,12.8650551,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1238,2149.4438477,-1750.1778564,12.7150574,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1238,2146.3095703,-1750.1096191,12.7150574,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1238,2143.9619141,-1749.2585449,12.7150574,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1238,2143.3496094,-1746.7462158,12.8650551,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1238,2143.5107422,-1744.0632324,12.8650551,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1306,2148.6970215,-1741.1007080,24.7350578,0.0000000,0.0000000,358.2500000); //
	CreateDynamicObject(1465,2145.5842285,-1743.4425049,13.7138319,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1465,2148.4641113,-1743.4016113,13.7124262,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1465,2151.3327637,-1743.3051758,13.7110252,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1466,2145.5871582,-1743.4268799,16.0320930,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1466,2151.3500977,-1743.3013916,16.0320930,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1428,2148.2197266,-1744.5153809,13.2658253,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1428,2149.6098633,-1743.2525635,16.3644867,0.0000000,0.0000000,268.0000000); //

	// Objects converted: 63

	
	// LSPD Interior
	CreateDynamicObject(19379,1469.3994141,-1754.0000000,3284.1999512,0.0000000,90.0000000,90.0000000); //object(sfw_boxwest12)(1)
	CreateDynamicObject(19379,1479.0000000,-1754.0000000,3284.1999512,0.0000000,90.0000000,90.0000000); //object(sfw_boxwest12)(2)
	CreateDynamicObject(1536,1475.6999512,-1748.8630371,3284.3000488,0.0000000,0.0000000,180.0000000); //object(gen_doorext15)(1)
	CreateDynamicObject(1536,1472.6992188,-1748.8994141,3284.3000488,0.0000000,0.0000000,0.0000000); //object(gen_doorext15)(2)
	CreateDynamicObject(19450,1464.5000000,-1753.5996094,3286.0000000,0.0000000,0.0000000,0.0000000); //object(cs_detrok10)(3)
	CreateDynamicObject(19450,1483.7998047,-1753.5996094,3286.0000000,0.0000000,0.0000000,0.0000000); //object(cs_detrok10)(4)
	CreateDynamicObject(18070,1474.1992188,-1755.8994141,3284.8000488,0.0000000,0.0000000,179.9945068); //object(gap_counter)(1)
	CreateDynamicObject(19379,1479.0000000,-1764.5000000,3284.1999512,0.0000000,90.0000000,90.0000000); //object(sfw_boxwest12)(3)
	CreateDynamicObject(19379,1469.3994141,-1764.5000000,3284.1999512,0.0000000,90.0000000,90.0000000); //object(sfw_boxwest12)(4)
	CreateDynamicObject(18070,1474.1999512,-1755.8000488,3287.1000977,0.0000000,179.9945068,179.9945068); //object(gap_counter)(3)
	CreateDynamicObject(19435,1477.8010254,-1756.5996094,3284.6000977,90.0000000,0.0000000,0.0000000); //object(cs_landbit_58_a)(1)
	CreateDynamicObject(19435,1477.8007812,-1755.0996094,3284.6000977,90.0000000,0.0000000,0.0000000); //object(cs_landbit_58_a)(3)
	CreateDynamicObject(19435,1476.1390381,-1753.4000244,3284.6000977,90.0000000,90.0000000,0.0000000); //object(cs_landbit_58_a)(4)
	CreateDynamicObject(19435,1472.6999512,-1753.4000244,3284.6000977,90.0000000,90.0000000,0.0000000); //object(cs_landbit_58_a)(5)
	CreateDynamicObject(19435,1472.2607422,-1753.4003906,3284.6000977,90.0000000,90.0000000,0.0000000); //object(cs_landbit_58_a)(6)
	CreateDynamicObject(19435,1470.5996094,-1755.0996094,3284.6000977,90.0000000,0.0000000,0.0000000); //object(cs_landbit_58_a)(7)
	CreateDynamicObject(19435,1470.5996094,-1756.5996094,3284.6000977,90.0000000,0.0000000,0.0000000); //object(cs_landbit_58_a)(8)
	CreateDynamicObject(19379,1479.0000000,-1754.0000000,3287.6999512,0.0000000,90.0000000,90.0000000); //object(sfw_boxwest12)(5)
	CreateDynamicObject(19379,1469.4000244,-1754.0000000,3287.6999512,0.0000000,90.0000000,90.0000000); //object(sfw_boxwest12)(6)
	CreateDynamicObject(19435,1477.8010254,-1756.5996094,3287.3000488,90.0000000,0.0000000,0.0000000); //object(cs_landbit_58_a)(9)
	CreateDynamicObject(19435,1477.7998047,-1755.0996094,3287.3000488,90.0000000,0.0000000,0.0000000); //object(cs_landbit_58_a)(10)
	CreateDynamicObject(19435,1476.0996094,-1753.3994141,3287.3000488,90.0000000,90.0000000,0.0000000); //object(cs_landbit_58_a)(11)
	CreateDynamicObject(19435,1472.6992188,-1753.3994141,3287.3000488,90.0000000,90.0000000,0.0000000); //object(cs_landbit_58_a)(12)
	CreateDynamicObject(19435,1472.3000488,-1753.4010010,3287.3000488,90.0000000,90.0000000,0.0000000); //object(cs_landbit_58_a)(13)
	CreateDynamicObject(19435,1470.5996094,-1755.0996094,3287.3000488,90.0000000,0.0000000,0.0000000); //object(cs_landbit_58_a)(14)
	CreateDynamicObject(19435,1470.6009522,-1756.5996094,3287.3000488,90.0000000,0.0000000,0.0000000); //object(cs_landbit_58_a)(15)
	CreateDynamicObject(19379,1459.7998047,-1764.5000000,3284.1999512,0.0000000,90.0000000,90.0000000); //object(sfw_boxwest12)(7)
	CreateDynamicObject(19379,1488.5996094,-1764.5000000,3284.1999512,0.0000000,90.0000000,90.0000000); //object(sfw_boxwest12)(8)
	CreateDynamicObject(19388,1483.7998047,-1763.1992188,3286.0000000,0.0000000,0.0000000,0.0000000); //object(road_sfw15)(1)
	CreateDynamicObject(19358,1464.5000000,-1760.0000000,3286.0000000,0.0000000,0.0000000,0.0000000); //object(road_sfw12)(1)
	CreateDynamicObject(19431,1465.3994141,-1758.2998047,3286.0000000,0.0000000,0.0000000,270.0000000); //object(cs_landbit_48_a)(3)
	CreateDynamicObject(19388,1467.8000488,-1758.3000488,3286.0000000,0.0000000,0.0000000,270.0000000); //object(road_sfw15)(2)
	CreateDynamicObject(19358,1471.0000000,-1758.3000488,3286.0000000,0.0000000,0.0000000,90.0000000); //object(road_sfw12)(2)
	CreateDynamicObject(19358,1477.3994141,-1758.2998047,3286.0000000,0.0000000,0.0000000,90.0000000); //object(road_sfw12)(3)
	CreateDynamicObject(19388,1480.5996094,-1758.2998047,3286.0000000,0.0000000,0.0000000,270.0000000); //object(road_sfw15)(3)
	CreateDynamicObject(19358,1483.7998047,-1766.3994141,3286.0000000,0.0000000,0.0000000,0.0000000); //object(road_sfw12)(4)
	CreateDynamicObject(19358,1483.7998047,-1760.0000000,3286.0000000,0.0000000,0.0000000,0.0000000); //object(road_sfw12)(5)
	CreateDynamicObject(19388,1464.5000000,-1763.1992188,3286.0000000,0.0000000,0.0000000,0.0000000); //object(road_sfw15)(4)
	CreateDynamicObject(19358,1464.5000000,-1766.3994141,3286.0000000,0.0000000,0.0000000,0.0000000); //object(road_sfw12)(6)
	CreateDynamicObject(19431,1483.0000000,-1768.0000000,3286.0000000,0.0000000,0.0000000,270.0000000); //object(cs_landbit_48_a)(4)
	CreateDynamicObject(19358,1479.0000000,-1769.5156250,3286.0000000,0.0000000,0.0000000,0.0000000); //object(road_sfw12)(7)
	CreateDynamicObject(19358,1477.3994141,-1768.0000000,3286.0000000,0.0000000,0.0000000,90.0000000); //object(road_sfw12)(8)
	CreateDynamicObject(14416,1474.0996094,-1771.0000000,3284.5000000,0.0000000,0.0000000,179.9945068); //object(carter-stairs07)(1)
	CreateDynamicObject(19450,1475.7998047,-1772.7290039,3286.0000000,0.0000000,0.0000000,0.0000000); //object(cs_detrok10)(3)
	CreateDynamicObject(19450,1472.5000000,-1772.7285156,3286.0000000,0.0000000,0.0000000,0.0000000); //object(cs_detrok10)(3)
	CreateDynamicObject(19379,1479.0000000,-1762.7998047,3287.7009277,0.0000000,90.0000000,90.0000000); //object(sfw_boxwest12)(5)
	CreateDynamicObject(19379,1469.3994141,-1762.7998047,3287.7009277,0.0000000,90.0000000,90.0000000); //object(sfw_boxwest12)(5)
	CreateDynamicObject(19379,1477.2998047,-1778.2998047,3287.6999512,0.0000000,90.0000000,90.0000000); //object(sfw_boxwest12)(5)
	CreateDynamicObject(19450,1467.7719727,-1773.0000000,3289.5000000,0.0000000,0.0000000,270.0000000); //object(cs_detrok10)(1)
	CreateDynamicObject(19450,1477.3000488,-1768.0000000,3289.5000000,0.0000000,0.0000000,270.0000000); //object(cs_detrok10)(1)
	CreateDynamicObject(19450,1480.5269775,-1773.0000000,3289.5000000,0.0000000,0.0000000,270.0000000); //object(cs_detrok10)(1)
	CreateDynamicObject(19450,1485.3000488,-1777.9000244,3289.5000000,0.0000000,0.0000000,0.0000000); //object(cs_detrok10)(4)
	CreateDynamicObject(19450,1463.0000000,-1777.9000244,3289.5000000,0.0000000,0.0000000,0.0000000); //object(cs_detrok10)(4)
	CreateDynamicObject(19379,1480.5000000,-1777.8994141,3291.1999512,0.0000000,90.0000000,90.0000000); //object(sfw_boxwest12)(5)
	CreateDynamicObject(19379,1470.9000244,-1777.9000244,3291.1999512,0.0000000,90.0000000,90.0000000); //object(sfw_boxwest12)(5)
	CreateDynamicObject(19379,1461.2998047,-1777.8994141,3291.1999512,0.0000000,90.0000000,90.0000000); //object(sfw_boxwest12)(5)
	CreateDynamicObject(19379,1470.9000244,-1767.4000244,3291.1999512,0.0000000,90.0000000,90.0000000); //object(sfw_boxwest12)(5)
	CreateDynamicObject(19450,1472.5000000,-1768.0996094,3289.5000000,0.0000000,0.0000000,0.0000000); //object(cs_detrok10)(4)
	CreateDynamicObject(19450,1475.8000488,-1768.0999756,3289.5000000,0.0000000,0.0000000,0.0000000); //object(cs_detrok10)(4)
	CreateDynamicObject(19379,1467.6992188,-1778.2998047,3287.6999512,0.0000000,90.0000000,90.0000000); //object(sfw_boxwest12)(5)
	CreateDynamicObject(19379,1486.9000244,-1778.3000488,3287.6999512,0.0000000,90.0000000,90.0000000); //object(sfw_boxwest12)(5)
	CreateDynamicObject(19450,1467.8000488,-1782.6999512,3289.5000000,0.0000000,0.0000000,270.0000000); //object(cs_detrok10)(1)
	CreateDynamicObject(19450,1480.5000000,-1782.6999512,3289.5000000,0.0000000,0.0000000,270.0000000); //object(cs_detrok10)(1)
	CreateDynamicObject(19388,1474.0999756,-1782.6999512,3289.5000000,0.0000000,0.0000000,270.0000000); //object(road_sfw15)(5)
	CreateDynamicObject(19379,1474.0996094,-1788.7998047,3287.6999512,0.0000000,90.0000000,90.0000000); //object(sfw_boxwest12)(5)
	CreateDynamicObject(19450,1478.7998047,-1787.5996094,3289.5000000,0.0000000,0.0000000,0.0000000); //object(cs_detrok10)(4)
	CreateDynamicObject(19450,1469.3994141,-1787.5996094,3289.5000000,0.0000000,0.0000000,0.0000000); //object(cs_detrok10)(4)
	CreateDynamicObject(19379,1474.0996094,-1788.3994141,3291.1999512,0.0000000,90.0000000,90.0000000); //object(sfw_boxwest12)(5)
	CreateDynamicObject(19431,1483.0000000,-1758.2998047,3286.0000000,0.0000000,0.0000000,270.0000000); //object(cs_landbit_48_a)(6)
	CreateDynamicObject(19431,1474.0999756,-1786.4000244,3289.5000000,0.0000000,0.0000000,180.0000000); //object(cs_landbit_48_a)(7)
	CreateDynamicObject(19431,1474.8129883,-1785.5999756,3289.5000000,0.0000000,0.0000000,90.0000000); //object(cs_landbit_48_a)(8)
	CreateDynamicObject(19388,1477.1999512,-1785.5999756,3289.5000000,0.0000000,0.0000000,270.0000000); //object(road_sfw15)(6)
	CreateDynamicObject(19431,1474.0996094,-1791.1992188,3289.5000000,0.0000000,0.0000000,179.9945068); //object(cs_landbit_48_a)(9)
	CreateDynamicObject(19358,1474.0996094,-1788.7998047,3289.5000000,0.0000000,0.0000000,0.0000000); //object(road_sfw12)(19)
	CreateDynamicObject(19431,1478.8000488,-1793.1999512,3289.5000000,0.0000000,0.0000000,179.9945068); //object(cs_landbit_48_a)(11)
	CreateDynamicObject(19388,1474.1992188,-1758.2998047,3286.0000000,0.0000000,0.0000000,270.0000000); //object(road_sfw15)(3)
	CreateDynamicObject(19358,1485.4000244,-1768.0000000,3286.0000000,0.0000000,0.0000000,90.0000000); //object(road_sfw12)(7)
	CreateDynamicObject(19358,1485.4000244,-1759.3000488,3286.0000000,0.0000000,0.0000000,90.0000000); //object(road_sfw12)(7)
	CreateDynamicObject(19358,1487.0000000,-1766.4000244,3286.0000000,0.0000000,0.0000000,0.0000000); //object(road_sfw12)(4)
	CreateDynamicObject(19388,1487.0000000,-1763.1999512,3286.0000000,0.0000000,0.0000000,0.0000000); //object(road_sfw15)(1)
	CreateDynamicObject(19358,1487.0000000,-1760.0000000,3286.0000000,0.0000000,0.0000000,0.0000000); //object(road_sfw12)(5)
	CreateDynamicObject(19379,1498.1999512,-1764.5000000,3284.1999512,0.0000000,90.0000000,90.0000000); //object(sfw_boxwest12)(8)
	CreateDynamicObject(19379,1507.8000488,-1764.5000000,3284.1999512,0.0000000,90.0000000,90.0000000); //object(sfw_boxwest12)(8)
	CreateDynamicObject(19379,1488.5999756,-1754.0000000,3284.1999512,0.0000000,90.0000000,90.0000000); //object(sfw_boxwest12)(8)
	CreateDynamicObject(19379,1498.1999512,-1754.0000000,3284.1999512,0.0000000,90.0000000,90.0000000); //object(sfw_boxwest12)(8)
	CreateDynamicObject(19379,1507.8000488,-1754.0000000,3284.1999512,0.0000000,90.0000000,90.0000000); //object(sfw_boxwest12)(8)
	CreateDynamicObject(19447,1487.0999756,-1756.8000488,3286.0000000,0.0000000,0.0000000,0.0000000); //object(cs_detrok13)(1)
	CreateDynamicObject(19385,1487.0999756,-1763.1999512,3286.0000000,0.0000000,0.0000000,0.0000000); //object(sfw_boxwest02)(1)
	CreateDynamicObject(19447,1492.0000000,-1769.6992188,3286.0000000,0.0000000,0.0000000,270.0000000); //object(cs_detrok13)(2)
	CreateDynamicObject(19355,1488.7998047,-1761.5000000,3286.0000000,0.0000000,0.0000000,90.0000000); //object(cs_landbit_12)(1)
	CreateDynamicObject(19355,1488.8000488,-1764.9000244,3286.0000000,0.0000000,0.0000000,90.0000000); //object(cs_landbit_12)(2)
	CreateDynamicObject(19385,1492.0000000,-1761.5000000,3286.0000000,0.0000000,0.0000000,90.0000000); //object(sfw_boxwest02)(2)
	CreateDynamicObject(19447,1490.3994141,-1756.5996094,3286.0000000,0.0000000,0.0000000,0.0000000); //object(cs_detrok13)(3)
	CreateDynamicObject(19385,1495.1992188,-1761.5000000,3286.0000000,0.0000000,0.0000000,90.0000000); //object(sfw_boxwest02)(6)
	CreateDynamicObject(19385,1498.3994141,-1761.5000000,3286.0000000,0.0000000,0.0000000,90.0000000); //object(sfw_boxwest02)(7)
	CreateDynamicObject(19385,1501.5999756,-1761.5000000,3286.0000000,0.0000000,0.0000000,90.0000000); //object(sfw_boxwest02)(8)
	CreateDynamicObject(19447,1493.5999756,-1756.6999512,3286.0000000,0.0000000,0.0000000,0.0000000); //object(cs_detrok13)(4)
	CreateDynamicObject(19447,1496.8000488,-1756.5999756,3286.0000000,0.0000000,0.0000000,0.0000000); //object(cs_detrok13)(5)
	CreateDynamicObject(19447,1500.0999756,-1756.5999756,3286.0000000,0.0000000,0.0000000,0.0000000); //object(cs_detrok13)(6)
	CreateDynamicObject(19447,1503.3000488,-1756.6999512,3286.0000000,0.0000000,0.0000000,0.0000000); //object(cs_detrok13)(7)
	CreateDynamicObject(19447,1503.2998047,-1766.2998047,3286.0000000,0.0000000,0.0000000,0.0000000); //object(cs_detrok13)(8)
	CreateDynamicObject(19385,1492.0000000,-1764.9000244,3286.0000000,0.0000000,0.0000000,90.0000000); //object(sfw_boxwest02)(9)
	CreateDynamicObject(19385,1495.1992188,-1764.8994141,3286.0000000,0.0000000,0.0000000,90.0000000); //object(sfw_boxwest02)(10)
	CreateDynamicObject(19385,1498.4000244,-1764.9000244,3286.0000000,0.0000000,0.0000000,90.0000000); //object(sfw_boxwest02)(11)
	CreateDynamicObject(19385,1501.5999756,-1764.9000244,3286.0000000,0.0000000,0.0000000,90.0000000); //object(sfw_boxwest02)(12)
	CreateDynamicObject(19447,1487.0996094,-1769.5996094,3286.0000000,0.0000000,0.0000000,0.0000000); //object(cs_detrok13)(9)
	CreateDynamicObject(19447,1501.5999756,-1769.6999512,3286.0000000,0.0000000,0.0000000,270.0000000); //object(cs_detrok13)(10)
	CreateDynamicObject(19447,1490.4000244,-1769.8000488,3286.0000000,0.0000000,0.0000000,0.0000000); //object(cs_detrok13)(11)
	CreateDynamicObject(19447,1493.5999756,-1769.8000488,3286.0000000,0.0000000,0.0000000,0.0000000); //object(cs_detrok13)(12)
	CreateDynamicObject(19447,1496.7998047,-1769.7998047,3286.0000000,0.0000000,0.0000000,0.0000000); //object(cs_detrok13)(13)
	CreateDynamicObject(19447,1500.0000000,-1769.8000488,3286.0000000,0.0000000,0.0000000,0.0000000); //object(cs_detrok13)(14)
	CreateDynamicObject(19447,1492.0000000,-1757.0999756,3286.0000000,0.0000000,0.0000000,270.0000000); //object(cs_detrok13)(15)
	CreateDynamicObject(19447,1501.5996094,-1757.0996094,3286.0000000,0.0000000,0.0000000,270.0000000); //object(cs_detrok13)(16)
	CreateDynamicObject(19379,1488.5996094,-1764.5000000,3287.6999512,0.0000000,90.0000000,90.0000000); //object(sfw_boxwest12)(8)
	CreateDynamicObject(19379,1498.1999512,-1764.5000000,3287.6999512,0.0000000,90.0000000,90.0000000); //object(sfw_boxwest12)(8)
	CreateDynamicObject(19379,1507.7998047,-1764.5000000,3287.6999512,0.0000000,90.0000000,90.0000000); //object(sfw_boxwest12)(8)
	CreateDynamicObject(19379,1507.8000488,-1754.0000000,3287.6999512,0.0000000,90.0000000,90.0000000); //object(sfw_boxwest12)(8)
	CreateDynamicObject(19379,1498.1999512,-1754.0000000,3287.6999512,0.0000000,90.0000000,90.0000000); //object(sfw_boxwest12)(8)
	CreateDynamicObject(19379,1488.5999756,-1754.0000000,3287.6999512,0.0000000,90.0000000,90.0000000); //object(sfw_boxwest12)(8)
	CreateDynamicObject(19450,1459.5999756,-1759.1999512,3286.0000000,0.0000000,0.0000000,270.0000000); //object(cs_detrok10)(1)
	CreateDynamicObject(19450,1459.6992188,-1768.0000000,3286.0000000,0.0000000,0.0000000,270.0000000); //object(cs_detrok10)(1)
	CreateDynamicObject(19450,1454.9000244,-1763.1999512,3286.0000000,0.0000000,0.0000000,0.0000000); //object(cs_detrok10)(3)
	CreateDynamicObject(19379,1459.8000488,-1764.5000000,3287.6999512,0.0000000,90.0000000,90.0000000); //object(sfw_boxwest12)(7)
	CreateDynamicObject(2008,1474.6999512,-1754.3000488,3284.4899902,0.0000000,0.0000000,0.0000000); //object(officedesk1)(1)
	CreateDynamicObject(2008,1472.5999756,-1754.3000488,3284.4899902,0.0000000,0.0000000,0.0000000); //object(officedesk1)(2)
	CreateDynamicObject(2607,1471.4000244,-1755.9000244,3284.8999023,0.0000000,0.0000000,270.0000000); //object(polce_desk2)(1)
	CreateDynamicObject(2007,1486.4000244,-1759.9000244,3284.3000488,0.0000000,0.0000000,0.0000000); //object(filing_cab_nu01)(1)
	CreateDynamicObject(2007,1485.4000244,-1759.9000244,3284.3000488,0.0000000,0.0000000,0.0000000); //object(filing_cab_nu01)(2)
	CreateDynamicObject(2007,1484.3994141,-1759.8994141,3284.3000488,0.0000000,0.0000000,0.0000000); //object(filing_cab_nu01)(3)
	CreateDynamicObject(2162,1471.8100586,-1758.0999756,3284.3850098,0.0000000,0.0000000,180.0000000); //object(med_office_unit_1)(1)
	CreateDynamicObject(2606,1473.1999512,-1754.4000244,3287.0000000,6.5000000,0.0000000,0.0000000); //object(cj_police_counter2)(1)
	CreateDynamicObject(2606,1475.1999512,-1754.4000244,3287.0000000,6.4984131,0.0000000,0.0000000); //object(cj_police_counter2)(3)
	CreateDynamicObject(2162,1476.6999512,-1754.1999512,3284.3850098,0.0000000,0.0000000,312.7445068); //object(med_office_unit_1)(2)
	CreateDynamicObject(1811,1483.1999512,-1752.4000244,3284.8999023,0.0000000,0.0000000,0.0000000); //object(med_din_chair_5)(1)
	CreateDynamicObject(1811,1483.1992188,-1753.1992188,3284.8999023,0.0000000,0.0000000,0.0000000); //object(med_din_chair_5)(2)
	CreateDynamicObject(1811,1483.1999512,-1754.0000000,3284.8999023,0.0000000,0.0000000,0.0000000); //object(med_din_chair_5)(3)
	CreateDynamicObject(1811,1483.1999512,-1754.8000488,3284.8999023,0.0000000,0.0000000,0.0000000); //object(med_din_chair_5)(4)
	CreateDynamicObject(1892,1472.9000244,-1749.5000000,3284.3000488,0.0000000,0.0000000,0.0000000); //object(security_gatsh)(1)
	CreateDynamicObject(1892,1474.5000000,-1749.5000000,3284.3000488,0.0000000,0.0000000,0.0000000); //object(security_gatsh)(2)
	CreateDynamicObject(2111,1482.6999512,-1750.9000244,3284.6999512,0.0000000,0.0000000,0.0000000); //object(low_dinning_5)(1)
	CreateDynamicObject(2816,1482.5999756,-1751.1999512,3285.1101074,0.0000000,0.0000000,0.0000000); //object(gb_bedmags01)(1)
	CreateDynamicObject(14401,1453.3000488,-1747.4000244,3284.6000977,0.0000000,0.0000000,180.0000000); //object(bench1)(1)
	CreateDynamicObject(14401,1443.0996094,-1773.5996094,3284.6000977,0.0000000,0.0000000,269.9945068); //object(bench1)(2)
	CreateDynamicObject(1502,1464.4394531,-1762.4150391,3284.2399902,0.0000000,0.0000000,270.0000000); //object(gen_doorint04)(1)
	CreateDynamicObject(14782,1461.3000488,-1759.6999512,3285.3000488,0.0000000,0.0000000,0.0000000); //object(int3int_boxing30)(1)
	CreateDynamicObject(14782,1455.6999512,-1760.0000000,3285.3000488,0.0000000,0.0000000,90.0000000); //object(int3int_boxing30)(4)
	CreateDynamicObject(2846,1456.0999756,-1760.5999756,3284.3000488,0.0000000,0.0000000,0.0000000); //object(gb_bedclothes05)(1)
	CreateDynamicObject(2614,1474.1500244,-1768.1250000,3289.5000000,0.0000000,0.0000000,0.0000000); //object(cj_us_flag)(1)
	CreateDynamicObject(2007,1463.0000000,-1767.4000244,3284.3000488,0.0000000,0.0000000,180.0000000); //object(filing_cab_nu01)(3)
	CreateDynamicObject(2007,1462.0000000,-1767.4000244,3284.3000488,0.0000000,0.0000000,179.9945068); //object(filing_cab_nu01)(3)
	CreateDynamicObject(2007,1461.0000000,-1767.4000244,3284.3000488,0.0000000,0.0000000,179.9945068); //object(filing_cab_nu01)(3)
	CreateDynamicObject(2400,1464.4000244,-1764.5999756,3284.3999023,0.0000000,0.0000000,270.0000000); //object(cj_sports_wall01)(1)
	CreateDynamicObject(2689,1464.0000000,-1765.0999756,3285.6999512,0.0000000,0.0000000,270.0000000); //object(cj_hoodie_2)(1)
	CreateDynamicObject(2704,1464.0999756,-1765.6999512,3285.6999512,0.0000000,0.0000000,270.0000000); //object(cj_hoodie_3)(1)
	CreateDynamicObject(19358,1482.1999512,-1769.5159912,3286.0000000,0.0000000,0.0000000,0.0000000); //object(road_sfw12)(7)
	CreateDynamicObject(14416,1480.5999756,-1772.8000488,3281.1000977,0.0000000,0.0000000,359.9945068); //object(carter-stairs07)(1)
	CreateDynamicObject(19358,1482.1999512,-1769.5999756,3282.5000000,0.0000000,0.0000000,0.0000000); //object(road_sfw12)(7)
	CreateDynamicObject(19358,1482.1999512,-1772.8000488,3282.5000000,0.0000000,0.0000000,0.0000000); //object(road_sfw12)(7)
	CreateDynamicObject(19358,1482.1999512,-1772.6999512,3286.0000000,0.0000000,0.0000000,0.0000000); //object(road_sfw12)(7)
	CreateDynamicObject(19358,1479.0000000,-1769.5999756,3282.5000000,0.0000000,0.0000000,0.0000000); //object(road_sfw12)(7)
	CreateDynamicObject(19358,1479.0000000,-1772.8000488,3282.5000000,0.0000000,0.0000000,0.0000000); //object(road_sfw12)(7)
	CreateDynamicObject(19358,1479.0000000,-1772.6999512,3286.0000000,0.0000000,0.0000000,0.0000000); //object(road_sfw12)(7)
	CreateDynamicObject(14416,1480.5000000,-1779.0999756,3277.6000977,0.0000000,0.0000000,359.9890137); //object(carter-stairs07)(1)
	CreateDynamicObject(19358,1482.1999512,-1776.0000000,3282.5000000,0.0000000,0.0000000,0.0000000); //object(road_sfw12)(7)
	CreateDynamicObject(19358,1479.0000000,-1776.0000000,3282.5000000,0.0000000,0.0000000,0.0000000); //object(road_sfw12)(7)
	CreateDynamicObject(19358,1482.1999512,-1775.9000244,3286.0000000,0.0000000,0.0000000,0.0000000); //object(road_sfw12)(7)
	CreateDynamicObject(19358,1479.0000000,-1775.9000244,3286.0000000,0.0000000,0.0000000,0.0000000); //object(road_sfw12)(7)
	CreateDynamicObject(19358,1480.5996094,-1777.5000000,3282.5000000,0.0000000,0.0000000,90.0000000); //object(road_sfw12)(7)
	CreateDynamicObject(19358,1480.5999756,-1777.5000000,3286.0000000,0.0000000,0.0000000,90.0000000); //object(road_sfw12)(7)
	CreateDynamicObject(19370,1480.5000000,-1769.5996094,3287.6999512,0.0000000,90.0000000,0.0000000); //object(freight_sfw15)(1)
	CreateDynamicObject(19370,1480.5000000,-1772.7998047,3287.6979981,0.0000000,90.0000000,0.0000000); //object(freight_sfw15)(2)
	CreateDynamicObject(19370,1480.5996094,-1776.0000000,3287.6979981,0.0000000,90.0000000,0.0000000); //object(freight_sfw15)(3)
	CreateDynamicObject(14416,1480.5000000,-1780.3000488,3277.6000977,0.0000000,0.0000000,359.9890137); //object(carter-stairs07)(1)
	CreateDynamicObject(1536,1479.0999756,-1777.4370117,3280.8000488,0.0000000,0.0000000,0.0000000); //object(gen_doorext15)(2)
	CreateDynamicObject(1536,1482.0999756,-1777.4000244,3280.8000488,0.0000000,0.0000000,180.0000000); //object(gen_doorext15)(2)
	CreateDynamicObject(1811,1464.0000000,-1777.8000488,3288.3999023,0.0000000,0.0000000,90.0000000); //object(med_din_chair_5)(5)
	CreateDynamicObject(1811,1464.9000244,-1777.8000488,3288.3999023,0.0000000,0.0000000,90.0000000); //object(med_din_chair_5)(6)
	CreateDynamicObject(1811,1465.8000488,-1777.8000488,3288.3999023,0.0000000,0.0000000,90.0000000); //object(med_din_chair_5)(7)
	CreateDynamicObject(1811,1466.6999512,-1777.8000488,3288.3999023,0.0000000,0.0000000,90.0000000); //object(med_din_chair_5)(9)
	CreateDynamicObject(1811,1467.5999756,-1777.8000488,3288.3999023,0.0000000,0.0000000,90.0000000); //object(med_din_chair_5)(10)
	CreateDynamicObject(1811,1467.5999756,-1776.0999756,3288.3999023,0.0000000,0.0000000,90.0000000); //object(med_din_chair_5)(11)
	CreateDynamicObject(1811,1466.6999512,-1776.0999756,3288.3999023,0.0000000,0.0000000,90.0000000); //object(med_din_chair_5)(12)
	CreateDynamicObject(1811,1465.8000488,-1776.0999756,3288.3999023,0.0000000,0.0000000,90.0000000); //object(med_din_chair_5)(13)
	CreateDynamicObject(1811,1464.9000244,-1776.0999756,3288.3999023,0.0000000,0.0000000,90.0000000); //object(med_din_chair_5)(14)
	CreateDynamicObject(1811,1464.0000000,-1776.0999756,3288.3999023,0.0000000,0.0000000,90.0000000); //object(med_din_chair_5)(15)
	CreateDynamicObject(1811,1467.5999756,-1774.5999756,3288.3999023,0.0000000,0.0000000,90.0000000); //object(med_din_chair_5)(16)
	CreateDynamicObject(1811,1466.6999512,-1774.5999756,3288.3999023,0.0000000,0.0000000,90.0000000); //object(med_din_chair_5)(17)
	CreateDynamicObject(1811,1465.9000244,-1774.5999756,3288.3999023,0.0000000,0.0000000,90.0000000); //object(med_din_chair_5)(18)
	CreateDynamicObject(1811,1465.0000000,-1774.5999756,3288.3999023,0.0000000,0.0000000,90.0000000); //object(med_din_chair_5)(19)
	CreateDynamicObject(1811,1464.0999756,-1774.5999756,3288.3999023,0.0000000,0.0000000,90.0000000); //object(med_din_chair_5)(20)
	CreateDynamicObject(3077,1466.8000488,-1781.8000488,3287.8000488,0.0000000,0.0000000,0.0000000); //object(nf_blackboard)(1)
	CreateDynamicObject(14532,1464.0996094,-1781.1992188,3288.8000488,0.0000000,0.0000000,349.9969482); //object(tv_stand_driv)(1)
	CreateDynamicObject(19358,1470.5000000,-1774.6999512,3289.5000000,0.0000000,0.0000000,0.0000000); //object(road_sfw12)(7)
	CreateDynamicObject(19388,1470.5000000,-1777.9000244,3289.5000000,0.0000000,0.0000000,0.0000000); //object(road_sfw15)(1)
	CreateDynamicObject(19358,1470.5000000,-1781.0999756,3289.5000000,0.0000000,0.0000000,0.0000000); //object(road_sfw12)(7)
	CreateDynamicObject(2357,1471.5996094,-1787.6992188,3288.1999512,0.0000000,0.0000000,270.0000000); //object(dunc_dinning)(1)
	CreateDynamicObject(1714,1513.0999756,-1837.5000000,3216.6999512,0.0000000,0.0000000,0.0000000); //object(kb_swivelchair1)(1)
	CreateDynamicObject(1714,1471.5999756,-1790.6999512,3287.8000488,0.0000000,0.0000000,180.0000000); //object(kb_swivelchair1)(2)
	CreateDynamicObject(1671,1470.4000244,-1788.9000244,3288.1999512,0.0000000,0.0000000,90.0000000); //object(swivelchair_a)(1)
	CreateDynamicObject(1671,1470.4000244,-1787.6999512,3288.1999512,0.0000000,0.0000000,90.0000000); //object(swivelchair_a)(2)
	CreateDynamicObject(1671,1470.4000244,-1786.5000000,3288.1999512,0.0000000,0.0000000,90.0000000); //object(swivelchair_a)(4)
	CreateDynamicObject(1671,1472.9000244,-1788.9000244,3288.1999512,0.0000000,0.0000000,270.0000000); //object(swivelchair_a)(5)
	CreateDynamicObject(1671,1472.9000244,-1787.6999512,3288.1999512,0.0000000,0.0000000,270.0000000); //object(swivelchair_a)(7)
	CreateDynamicObject(1671,1472.9000244,-1786.5000000,3288.1999512,0.0000000,0.0000000,270.0000000); //object(swivelchair_a)(9)
	CreateDynamicObject(14532,1470.0996094,-1791.5996094,3288.8000488,0.0000000,0.0000000,337.9943848); //object(tv_stand_driv)(1)
	CreateDynamicObject(1671,1475.1999512,-1790.4000244,3288.1999512,0.0000000,0.0000000,180.0000000); //object(swivelchair_a)(10)
	CreateDynamicObject(2165,1478.1999512,-1790.0999756,3287.8000488,0.0000000,0.0000000,270.0000000); //object(med_office_desk_1)(1)
	CreateDynamicObject(2166,1477.1999512,-1788.0999756,3287.8000488,0.0000000,0.0000000,270.0000000); //object(med_office_desk_2)(1)
	CreateDynamicObject(2173,1474.6999512,-1789.5000000,3287.8000488,0.0000000,0.0000000,0.0000000); //object(med_office_desk_3)(1)
	CreateDynamicObject(1671,1477.2998047,-1790.6992188,3288.1999512,0.0000000,0.0000000,90.0000000); //object(swivelchair_a)(11)
	CreateDynamicObject(1671,1475.0999756,-1788.5000000,3288.1999512,0.0000000,0.0000000,358.2445068); //object(swivelchair_a)(12)
	CreateDynamicObject(2186,1476.5999756,-1773.5999756,3287.8000488,0.0000000,0.0000000,0.0000000); //object(photocopier_1)(1)
	CreateDynamicObject(2612,1474.2230225,-1790.4000244,3289.6000977,0.0000000,0.0000000,90.0000000); //object(police_nb2)(1)
	CreateDynamicObject(2611,1474.2239990,-1787.8000488,3289.6201172,0.0000000,0.0000000,90.0000000); //object(police_nb1)(1)
	CreateDynamicObject(1502,1476.4599609,-1785.6199951,3287.7351074,0.0000000,0.0000000,0.0000000); //object(gen_doorint04)(1)
	CreateDynamicObject(2165,1479.1999512,-1775.5999756,3287.8000488,0.0000000,0.0000000,90.0000000); //object(med_office_desk_1)(2)
	CreateDynamicObject(2165,1479.3000488,-1778.5000000,3287.8000488,0.0000000,0.0000000,90.0000000); //object(med_office_desk_1)(3)
	CreateDynamicObject(2165,1479.4000244,-1781.5000000,3287.8000488,0.0000000,0.0000000,90.0000000); //object(med_office_desk_1)(4)
	CreateDynamicObject(2165,1482.3000488,-1775.5999756,3287.8000488,0.0000000,0.0000000,90.0000000); //object(med_office_desk_1)(5)
	CreateDynamicObject(2165,1482.4000244,-1778.5000000,3287.8000488,0.0000000,0.0000000,90.0000000); //object(med_office_desk_1)(6)
	CreateDynamicObject(2165,1482.5000000,-1781.5000000,3287.8000488,0.0000000,0.0000000,90.0000000); //object(med_office_desk_1)(7)
	CreateDynamicObject(1671,1483.1999512,-1775.0000000,3288.1999512,0.0000000,0.0000000,270.0000000); //object(swivelchair_a)(13)
	CreateDynamicObject(1671,1480.1999512,-1775.0000000,3288.1999512,0.0000000,0.0000000,270.0000000); //object(swivelchair_a)(14)
	CreateDynamicObject(1671,1483.3000488,-1778.0000000,3288.1999512,0.0000000,0.0000000,270.0000000); //object(swivelchair_a)(15)
	CreateDynamicObject(1671,1483.5000000,-1781.0000000,3288.1999512,0.0000000,0.0000000,270.0000000); //object(swivelchair_a)(16)
	CreateDynamicObject(1671,1480.4000244,-1781.0999756,3288.1999512,0.0000000,0.0000000,270.0000000); //object(swivelchair_a)(17)
	CreateDynamicObject(1671,1480.1999512,-1778.0000000,3288.1999512,0.0000000,0.0000000,270.0000000); //object(swivelchair_a)(18)
	CreateDynamicObject(2186,1474.7998047,-1786.1992188,3287.8000488,0.0000000,0.0000000,0.0000000); //object(photocopier_1)(2)
	CreateDynamicObject(2007,1471.1999512,-1773.6999512,3287.8000488,0.0000000,0.0000000,90.0000000); //object(filing_cab_nu01)(3)
	CreateDynamicObject(2007,1471.1999512,-1774.6999512,3287.8000488,0.0000000,0.0000000,90.0000000); //object(filing_cab_nu01)(3)
	CreateDynamicObject(2007,1471.1999512,-1775.6999512,3287.8000488,0.0000000,0.0000000,90.0000000); //object(filing_cab_nu01)(3)
	CreateDynamicObject(2166,1471.9000244,-1779.0999756,3287.8000488,0.0000000,0.0000000,270.0000000); //object(med_office_desk_2)(2)
	CreateDynamicObject(2165,1472.9000244,-1781.0999756,3287.8000488,0.0000000,0.0000000,270.0000000); //object(med_office_desk_1)(8)
	CreateDynamicObject(1714,1471.6999512,-1781.6999512,3287.8000488,0.0000000,0.0000000,89.9945068); //object(kb_swivelchair1)(3)
	CreateDynamicObject(1800,1492.6999512,-1760.8000488,3284.3000488,0.0000000,0.0000000,0.0000000); //object(low_bed_1)(1)
	CreateDynamicObject(1800,1495.9000244,-1760.8000488,3284.3000488,0.0000000,0.0000000,0.0000000); //object(low_bed_1)(2)
	CreateDynamicObject(1800,1499.1999512,-1760.8000488,3284.3000488,0.0000000,0.0000000,0.0000000); //object(low_bed_1)(3)
	CreateDynamicObject(1800,1502.4000244,-1760.8000488,3284.3000488,0.0000000,0.0000000,0.0000000); //object(low_bed_1)(4)
	CreateDynamicObject(1800,1491.0000000,-1770.5999756,3284.3000488,0.0000000,0.0000000,0.0000000); //object(low_bed_1)(5)
	CreateDynamicObject(1800,1494.1999512,-1770.5000000,3284.3000488,0.0000000,0.0000000,0.0000000); //object(low_bed_1)(6)
	CreateDynamicObject(1800,1497.4000244,-1770.5000000,3284.3000488,0.0000000,0.0000000,0.0000000); //object(low_bed_1)(7)
	CreateDynamicObject(1800,1500.5999756,-1770.5999756,3284.3000488,0.0000000,0.0000000,0.0000000); //object(low_bed_1)(8)
	CreateDynamicObject(2738,1500.5999756,-1766.0999756,3284.8999023,0.0000000,0.0000000,90.0000000); //object(cj_toilet_bs)(1)
	CreateDynamicObject(2738,1497.3000488,-1766.0999756,3284.8999023,0.0000000,0.0000000,90.0000000); //object(cj_toilet_bs)(2)
	CreateDynamicObject(2738,1494.0999756,-1766.0999756,3284.8999023,0.0000000,0.0000000,90.0000000); //object(cj_toilet_bs)(3)
	CreateDynamicObject(2738,1490.9000244,-1766.0999756,3284.8999023,0.0000000,0.0000000,90.0000000); //object(cj_toilet_bs)(4)
	CreateDynamicObject(2738,1491.0000000,-1759.9000244,3284.8999023,0.0000000,0.0000000,90.0000000); //object(cj_toilet_bs)(5)
	CreateDynamicObject(2738,1494.0999756,-1760.0000000,3284.8999023,0.0000000,0.0000000,90.0000000); //object(cj_toilet_bs)(6)
	CreateDynamicObject(2738,1497.3000488,-1760.0000000,3284.8999023,0.0000000,0.0000000,90.0000000); //object(cj_toilet_bs)(7)
	CreateDynamicObject(2738,1500.5999756,-1759.9000244,3284.8999023,0.0000000,0.0000000,90.0000000); //object(cj_toilet_bs)(8)
	CreateDynamicObject(2524,1500.6999512,-1758.5999756,3284.3000488,0.0000000,0.0000000,90.0000000); //object(cj_b_sink4)(1)
	CreateDynamicObject(2524,1497.4000244,-1758.6999512,3284.3000488,0.0000000,0.0000000,90.0000000); //object(cj_b_sink4)(2)
	CreateDynamicObject(2524,1494.1999512,-1758.8000488,3284.3000488,0.0000000,0.0000000,90.0000000); //object(cj_b_sink4)(3)
	CreateDynamicObject(2524,1491.0000000,-1758.9000244,3284.3000488,0.0000000,0.0000000,90.0000000); //object(cj_b_sink4)(4)
	CreateDynamicObject(2524,1493.0000000,-1767.5999756,3284.3000488,0.0000000,0.0000000,270.0000000); //object(cj_b_sink4)(5)
	CreateDynamicObject(2524,1496.1999512,-1767.5999756,3284.3000488,0.0000000,0.0000000,270.0000000); //object(cj_b_sink4)(6)
	CreateDynamicObject(2524,1499.4000244,-1767.5999756,3284.3000488,0.0000000,0.0000000,270.0000000); //object(cj_b_sink4)(7)
	CreateDynamicObject(2524,1502.6999512,-1767.5999756,3284.3000488,0.0000000,0.0000000,270.0000000); //object(cj_b_sink4)(8)
	CreateDynamicObject(2007,1493.0000000,-1760.5999756,3284.3000488,0.0000000,0.0000000,270.0000000); //object(filing_cab_nu01)(3)
	CreateDynamicObject(2007,1496.1999512,-1760.5000000,3284.3000488,0.0000000,0.0000000,270.0000000); //object(filing_cab_nu01)(3)
	CreateDynamicObject(2007,1499.5000000,-1760.4000244,3284.3000488,0.0000000,0.0000000,270.0000000); //object(filing_cab_nu01)(3)
	CreateDynamicObject(2007,1502.6999512,-1760.3000488,3284.3000488,0.0000000,0.0000000,270.0000000); //object(filing_cab_nu01)(3)
	CreateDynamicObject(2007,1502.6999512,-1766.3000488,3284.3000488,0.0000000,0.0000000,270.0000000); //object(filing_cab_nu01)(3)
	CreateDynamicObject(2007,1499.4000244,-1766.3000488,3284.3000488,0.0000000,0.0000000,270.0000000); //object(filing_cab_nu01)(3)
	CreateDynamicObject(2007,1496.1999512,-1766.3000488,3284.3000488,0.0000000,0.0000000,270.0000000); //object(filing_cab_nu01)(3)
	CreateDynamicObject(2007,1493.0000000,-1766.3000488,3284.3000488,0.0000000,0.0000000,270.0000000); //object(filing_cab_nu01)(3)
	CreateDynamicObject(19450,1467.5999756,-1768.0009766,3286.0000000,0.0000000,0.0000000,270.0000000); //object(cs_detrok10)(1)
	CreateDynamicObject(1811,1472.3000488,-1758.9000244,3284.8999023,0.0000000,0.0000000,90.0000000); //object(med_din_chair_5)(2)
	CreateDynamicObject(1811,1471.5000000,-1758.9000244,3284.8999023,0.0000000,0.0000000,90.0000000); //object(med_din_chair_5)(2)
	CreateDynamicObject(1811,1470.6999512,-1758.9000244,3284.8999023,0.0000000,0.0000000,90.0000000); //object(med_din_chair_5)(2)
	CreateDynamicObject(1811,1469.9000244,-1758.9000244,3284.8999023,0.0000000,0.0000000,90.0000000); //object(med_din_chair_5)(2)
	CreateDynamicObject(18608,1473.5000000,-1763.1999512,3288.5000000,0.0000000,0.0000000,270.0000000); //object(counts_lights01)(1)
	CreateDynamicObject(18608,1452.0999756,-1763.8000488,3288.5000000,0.0000000,0.0000000,270.0000000); //object(counts_lights01)(2)
	CreateDynamicObject(18608,1474.8000488,-1756.4000244,3288.5000000,0.0000000,0.0000000,270.0000000); //object(counts_lights01)(3)
	CreateDynamicObject(18608,1470.9000244,-1750.9000244,3288.5000000,0.0000000,0.0000000,270.0000000); //object(counts_lights01)(4)
	CreateDynamicObject(18608,1474.6999512,-1777.8000488,3292.1999512,0.0000000,0.0000000,270.0000000); //object(counts_lights01)(5)
	CreateDynamicObject(18608,1464.0999756,-1786.6999512,3292.1999512,0.0000000,0.0000000,270.0000000); //object(counts_lights01)(6)
	CreateDynamicObject(18608,1483.8994141,-1788.8994141,3292.1999512,0.0000000,0.0000000,270.0000000); //object(counts_lights01)(7)
	CreateDynamicObject(18608,1492.8000488,-1763.1999512,3288.5000000,0.0000000,0.0000000,270.0000000); //object(counts_lights01)(8)
	CreateDynamicObject(1886,1465.0999756,-1757.5999756,3287.6999512,8.4999084,0.2527771,139.7126465); //object(shop_sec_cam)(1)
	CreateDynamicObject(1886,1483.4000244,-1757.8000488,3287.5000000,8.4979248,0.2526855,219.7076416); //object(shop_sec_cam)(2)
	CreateDynamicObject(1886,1502.6999512,-1764.4000244,3287.8000488,12.4978943,0.2559814,243.6865234); //object(shop_sec_cam)(3)
	CreateDynamicObject(1886,1465.1992188,-1767.5000000,3287.8000488,8.4979248,0.2526855,123.7005615); //object(shop_sec_cam)(4)
	CreateDynamicObject(19431,1469.4000244,-1793.1999512,3289.5000000,0.0000000,0.0000000,179.9945068); //object(cs_landbit_48_a)(11)
	CreateDynamicObject(19431,1474.0996094,-1792.7998047,3289.5000000,0.0000000,0.0000000,179.9945068); //object(cs_landbit_48_a)(11)
	CreateDynamicObject(19404,1471.6999512,-1793.5000000,3289.5000000,0.0000000,0.0000000,270.0000000); //object(boigagr_sfw)(1)
	CreateDynamicObject(19431,1474.0999756,-1793.5000000,3289.5000000,0.0000000,0.0000000,90.0000000); //object(cs_landbit_48_a)(11)
	CreateDynamicObject(19431,1469.3000488,-1793.5000000,3289.5000000,0.0000000,0.0000000,90.0000000); //object(cs_landbit_48_a)(11)
	CreateDynamicObject(19404,1476.5000000,-1793.5000000,3289.5000000,0.0000000,0.0000000,270.0000000); //object(boigagr_sfw)(2)
	CreateDynamicObject(19431,1478.9000244,-1793.5000000,3289.5000000,0.0000000,0.0000000,90.0000000); //object(cs_landbit_48_a)(11)
	CreateDynamicObject(4108,1480.5000000,-1805.9000244,3287.8999023,0.0000000,0.0000000,270.0000000); //object(roads01b_lan)(1)
	CreateDynamicObject(717,1477.0999756,-1805.9000244,3284.1000977,0.0000000,0.0000000,92.0000000); //object(sm_bevhiltreepv)(1)
	CreateDynamicObject(717,1486.5999756,-1805.8000488,3284.1000977,0.0000000,0.0000000,91.9995117); //object(sm_bevhiltreepv)(2)
	CreateDynamicObject(717,1496.5999756,-1805.6999512,3284.1000977,0.0000000,0.0000000,91.9995117); //object(sm_bevhiltreepv)(3)
	CreateDynamicObject(717,1508.8000488,-1805.5999756,3284.1000977,0.0000000,0.0000000,91.9995117); //object(sm_bevhiltreepv)(4)
	CreateDynamicObject(717,1520.5999756,-1805.5000000,3284.1000977,0.0000000,0.0000000,91.9995117); //object(sm_bevhiltreepv)(5)
	CreateDynamicObject(717,1467.8000488,-1805.9000244,3284.1000977,0.0000000,0.0000000,91.9995117); //object(sm_bevhiltreepv)(6)
	CreateDynamicObject(717,1457.0999756,-1805.5999756,3284.1000977,0.0000000,0.0000000,91.9995117); //object(sm_bevhiltreepv)(7)
	CreateDynamicObject(717,1445.3000488,-1805.1999512,3284.1000977,0.0000000,0.0000000,91.9995117); //object(sm_bevhiltreepv)(8)
	CreateDynamicObject(717,1434.9000244,-1805.3000488,3284.1000977,0.0000000,0.0000000,91.9995117); //object(sm_bevhiltreepv)(9)
	CreateDynamicObject(717,1421.9000244,-1805.6999512,3284.1000977,0.0000000,0.0000000,92.0000000); //object(sm_bevhiltreepv)(10)
	CreateDynamicObject(6199,1450.6999512,-1831.0999756,3295.8999023,0.0000000,0.0000000,4.7500000); //object(gaz27_law)(1)
	CreateDynamicObject(6199,1500.5999756,-1831.3000488,3295.8999023,0.0000000,0.0000000,4.7460938); //object(gaz27_law)(2)
	CreateDynamicObject(6364,1551.5999756,-1819.5000000,3308.1999512,0.0000000,0.0000000,68.0000000); //object(sunset07_law2)(1)
	CreateDynamicObject(6364,1568.6999512,-1845.8000488,3308.1999512,0.0000000,0.0000000,82.9998779); //object(sunset07_law2)(2)
	CreateDynamicObject(6391,1403.5999756,-1822.8000488,3327.6000977,0.0000000,0.0000000,97.0000000); //object(sanclifft05_law2)(1)
	CreateDynamicObject(3858,1474.5000000,-1793.5000000,3290.6999512,0.0000000,0.0000000,225.0000000); //object(ottosmash1)(1)
	CreateDynamicObject(3858,1474.5000000,-1793.5000000,3290.6999512,0.0000000,0.0000000,44.5000000); //object(ottosmash1)(2)
	CreateDynamicObject(2559,1468.9000244,-1749.3000488,3285.5000000,0.0000000,0.0000000,0.0000000); //object(curtain_1_open)(1)
	CreateDynamicObject(2559,1477.0000000,-1793.0000000,3289.0000000,0.0000000,0.0000000,179.9945068); //object(curtain_1_open)(2)
	CreateDynamicObject(4150,1484.9000244,-1741.1999512,3284.1999512,0.0000000,0.0000000,270.0000000); //object(roads14_lan)(1)
	CreateDynamicObject(19358,1482.1999512,-1748.8000488,3286.0000000,0.0000000,0.0000000,90.0000000); //object(road_sfw12)(3)
	CreateDynamicObject(19404,1479.0000000,-1748.8000488,3286.0000000,0.0000000,0.0000000,270.0000000); //object(boigagr_sfw)(3)
	CreateDynamicObject(19358,1475.8000488,-1748.8000488,3286.0000000,0.0000000,0.0000000,90.0000000); //object(road_sfw12)(3)
	CreateDynamicObject(19358,1472.5999756,-1748.8000488,3286.0000000,0.0000000,0.0000000,90.0000000); //object(road_sfw12)(3)
	CreateDynamicObject(19404,1469.4000244,-1748.8000488,3286.0000000,0.0000000,0.0000000,270.0000000); //object(boigagr_sfw)(4)
	CreateDynamicObject(19358,1466.1999512,-1748.8000488,3286.0000000,0.0000000,0.0000000,90.0000000); //object(road_sfw12)(3)
	CreateDynamicObject(3858,1474.1999512,-1748.8000488,3285.3000488,0.0000000,0.0000000,44.9946289); //object(ottosmash1)(3)
	CreateDynamicObject(3858,1474.1999512,-1748.8000488,3285.3000488,0.0000000,0.0000000,224.9945068); //object(ottosmash1)(4)
	CreateDynamicObject(2559,1472.1992188,-1793.0000000,3289.0000000,0.0000000,0.0000000,179.9945068); //object(curtain_1_open)(3)
	CreateDynamicObject(2559,1478.5000000,-1749.3000488,3285.5000000,0.0000000,0.0000000,0.0000000); //object(curtain_1_open)(4)
	CreateDynamicObject(4186,1454.9000244,-1689.0999756,3291.3000488,0.0000000,0.0000000,270.0000000); //object(pershingsq2_lan)(1)
	CreateDynamicObject(3985,1516.5000000,-1689.0999756,3283.8000488,0.0000000,0.0000000,270.0000000); //object(pershingsq1_lan)(1)
	CreateDynamicObject(713,1441.1999512,-1707.3000488,3281.1000977,0.0000000,0.0000000,0.0000000); //object(veg_bevtree1)(1)
	CreateDynamicObject(713,1527.6999512,-1710.8000488,3281.8000488,0.0000000,0.0000000,0.0000000); //object(veg_bevtree1)(2)
	CreateDynamicObject(713,1482.8000488,-1693.6999512,3285.3000488,0.0000000,0.0000000,0.0000000); //object(veg_bevtree1)(3)
	CreateDynamicObject(4016,1585.3000488,-1717.9000244,3292.1000977,0.0000000,0.0000000,270.0000000); //object(fighotbase_lan)(1)
	CreateDynamicObject(4006,1490.5000000,-1642.5999756,3304.5000000,0.0000000,0.0000000,270.0000000); //object(eastcolumb1_lan)(1)
	CreateDynamicObject(4008,1558.1999512,-1651.8000488,3292.0000000,0.0000000,0.0000000,272.0000000); //object(decoblok1_lan)(1)
	CreateDynamicObject(4005,1433.4000244,-1656.8000488,3297.8000488,0.0000000,0.0000000,270.0000000); //object(decoblok2_lan)(1)
	CreateDynamicObject(3980,1370.8000488,-1719.8000488,3294.0000000,0.0000000,0.0000000,270.0000000); //object(lacityhall1_lan)(1)
	CreateDynamicObject(4163,1415.8000488,-1678.5000000,3284.3000488,0.0000000,0.0000000,270.0000000); //object(roads24_lan)(1)
	CreateDynamicObject(4002,1360.5000000,-1717.6999512,3326.6000977,0.0000000,0.0000000,270.0000000); //object(lacityhall2_lan)(1)
	CreateDynamicObject(713,1422.1999512,-1669.0999756,3255.6000977,28.0000000,0.0000000,114.0000000); //object(veg_bevtree1)(4)
	
	//All Saints Hospital Exterior Edit (By: xmathewx75 AKA Vick Ross)
	//Permission to edit granted, do not remove credits!
	CreateDynamicObject(970,1190.1500000,-1383.0400000,12.9800000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(970,1190.1500000,-1378.8600000,12.9800000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(970,1190.1500000,-1374.6900000,12.9800000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(970,1190.1500000,-1370.5200000,12.9800000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(970,1190.1500000,-1366.3500000,12.9800000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(970,1190.1500000,-1362.1800000,12.9800000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(970,1190.1500000,-1358.0000000,12.9800000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(970,1190.1500000,-1353.8300000,12.9800000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(970,1190.1500000,-1349.6600000,12.9800000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(970,1190.1500000,-1345.4900000,12.9800000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(970,1190.1500000,-1332.9700000,12.9800000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(970,1190.1500000,-1328.8000000,12.9800000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(970,1190.1500000,-1319.4100000,12.9800000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(970,1190.1500000,-1315.2400000,12.9800000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(970,1190.1500000,-1302.7200000,12.9800000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(970,1190.1500000,-1298.5500000,12.9800000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(970,1190.1500000,-1294.3800000,12.9800000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(970,1211.4700000,-1383.0500000,12.9800000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(970,1211.4700000,-1378.8800000,12.9800000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(970,1211.4700000,-1374.7100000,12.9800000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(970,1211.4700000,-1370.5400000,12.9800000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(970,1211.4700000,-1366.3600000,12.9800000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(970,1211.4700000,-1362.1900000,12.9800000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(970,1211.4700000,-1358.0200000,12.9800000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(970,1211.4700000,-1353.8500000,12.9800000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(970,1211.4700000,-1349.6800000,12.9800000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(970,1211.4700000,-1345.5000000,12.9800000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(970,1211.4700000,-1341.3300000,12.9800000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(970,1211.4700000,-1337.1600000,12.9800000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(970,1211.4700000,-1332.9900000,12.9800000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(970,1211.4700000,-1328.8200000,12.9800000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(970,1211.4700000,-1324.6400000,12.9800000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(970,1211.4700000,-1320.4700000,12.9800000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(970,1211.4700000,-1316.3000000,12.9800000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(970,1211.4700000,-1312.1300000,12.9800000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(970,1211.4700000,-1307.9600000,12.9800000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(970,1211.4700000,-1303.7800000,12.9800000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(970,1211.4700000,-1299.6100000,12.9800000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(970,1211.4700000,-1295.4400000,12.9800000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(19425,1206.3100000,-1380.9400000,12.3800000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19425,1206.3100000,-1362.3200000,12.3800000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19425,1206.3100000,-1345.0300000,12.3800000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19425,1206.3100000,-1327.0100000,12.3800000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19425,1206.3100000,-1307.7800000,12.3800000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19425,1195.7300000,-1380.9400000,12.3800000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19425,1195.5800000,-1362.3200000,12.3800000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19425,1195.8800000,-1345.0300000,12.3800000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19425,1196.0300000,-1327.0100000,12.3800000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19425,1195.8800000,-1307.7800000,12.3800000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(16949,1173.5300000,-1322.9200000,18.4300000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1649,1172.9100000,-1320.5000000,20.0400000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1649,1172.9100000,-1324.9400000,20.0400000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1649,1172.9100000,-1320.5000000,23.3000000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1649,1172.9100000,-1320.5000000,26.5700000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1649,1172.9100000,-1320.5000000,29.8300000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1649,1172.9100000,-1324.9400000,23.3000000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1649,1172.9100000,-1324.9400000,26.5700000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1649,1172.9100000,-1324.9400000,29.8300000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1649,1172.9100000,-1328.9100000,20.0400000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1649,1172.9100000,-1328.9100000,23.3000000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1649,1172.9100000,-1328.9100000,26.5700000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1649,1172.9100000,-1328.9100000,29.8300000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1649,1172.9100000,-1332.8900000,20.0400000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1649,1172.9100000,-1332.8900000,23.3000000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1649,1172.9100000,-1332.8900000,26.5700000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1649,1172.9100000,-1332.8900000,29.8300000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1649,1172.9100000,-1336.8700000,20.0400000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1649,1172.9100000,-1336.8700000,23.3000000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1649,1172.9100000,-1336.8700000,26.5700000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1649,1172.9100000,-1336.8700000,29.8300000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1649,1172.9100000,-1340.5600000,20.0400000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1649,1172.9100000,-1340.5600000,23.3000000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1649,1172.9100000,-1340.5600000,26.5700000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1649,1172.9100000,-1340.5600000,29.8300000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1649,1172.9100000,-1316.2400000,20.0400000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1649,1172.9100000,-1316.2400000,23.3000000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1649,1172.9100000,-1316.2400000,26.5700000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1649,1172.9100000,-1316.2400000,29.8300000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1649,1172.9200000,-1311.9800000,20.0400000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1649,1172.9200000,-1311.9800000,23.3100000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1649,1172.9200000,-1311.9800000,26.5900000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1649,1172.9200000,-1311.9800000,29.8700000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1649,1172.9200000,-1307.6500000,20.0400000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1649,1172.9200000,-1307.6500000,23.3100000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1649,1172.9200000,-1307.6500000,29.8700000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1649,1172.9200000,-1307.6500000,26.5900000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(3440,1172.8500000,-1305.5400000,20.7400000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.8500000,-1305.5400000,25.3600000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.8500000,-1305.5400000,29.3800000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.8500000,-1309.7200000,29.3800000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.8500000,-1314.1900000,29.3800000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.8500000,-1318.5100000,29.3800000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.8500000,-1322.6800000,29.3800000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.8500000,-1326.8500000,29.3800000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.8500000,-1331.0200000,29.3800000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.8500000,-1334.9000000,29.3800000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.8500000,-1338.7700000,29.3800000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.8500000,-1342.5000000,29.3800000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.8500000,-1342.5000000,25.0600000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.8500000,-1342.5000000,20.4400000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.8500000,-1338.7700000,25.0600000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.8500000,-1338.7700000,20.5900000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.8500000,-1334.9000000,25.0600000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.8500000,-1334.9000000,20.4400000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.8500000,-1331.0200000,25.0600000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.8500000,-1331.0200000,20.5900000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.8500000,-1326.8500000,25.2100000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.8500000,-1326.8500000,20.7400000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.8500000,-1322.6800000,25.0600000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.8500000,-1322.6800000,20.4400000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.8500000,-1318.5100000,25.2100000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.8500000,-1318.5100000,20.7400000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.8500000,-1314.1900000,24.7600000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.8500000,-1314.1900000,20.4400000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.8500000,-1309.7200000,24.7600000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.8500000,-1309.7200000,20.4400000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.8600000,-1307.6700000,31.7000000,90.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.8600000,-1312.2900000,31.7000000,90.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.8600000,-1316.1600000,31.7000000,90.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.8600000,-1320.6300000,31.7000000,90.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.8600000,-1324.5000000,31.7000000,90.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.8600000,-1328.6800000,31.7000000,90.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.8600000,-1333.0000000,31.7000000,90.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.8600000,-1336.5700000,31.7000000,90.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.8600000,-1340.3000000,31.7000000,90.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1649,1172.9100000,-1344.8800000,21.9600000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1649,1172.9100000,-1344.8800000,18.6800000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1649,1172.9100000,-1349.2000000,18.6800000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1649,1172.9400000,-1353.5200000,18.6800000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1649,1172.9100000,-1349.2000000,21.9600000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1649,1172.9600000,-1353.5200000,21.9600000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1649,1172.9600000,-1357.8400000,21.9600000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1649,1172.9900000,-1362.1600000,21.9600000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1649,1172.9600000,-1357.8400000,18.6800000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1649,1173.0000000,-1366.4800000,21.9600000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1649,1172.9800000,-1362.1600000,18.6800000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1649,1173.0000000,-1366.5600000,18.6800000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1649,1173.0000000,-1366.5600000,15.4100000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1649,1173.0100000,-1366.5600000,12.1300000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1649,1172.9800000,-1362.1600000,15.3800000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1649,1172.9800000,-1362.1600000,12.1500000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1649,1172.9600000,-1357.8400000,15.3800000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1649,1172.9700000,-1357.8400000,12.1100000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1649,1172.9400000,-1353.5200000,15.3800000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(1649,1172.9500000,-1353.5200000,12.1500000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(3440,1172.8500000,-1347.0400000,20.7300000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.8500000,-1351.4400000,20.7300000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.8500000,-1355.7000000,21.1500000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.8500000,-1355.7000000,16.8900000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.8300000,-1355.7000000,8.0900000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.8500000,-1355.7000000,12.2100000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.8500000,-1359.9600000,12.2100000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.8500000,-1364.5100000,12.2100000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1173.0700000,-1367.3700000,12.2100000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1173.0700000,-1367.3700000,16.7500000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1173.0700000,-1367.3700000,21.1500000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.8500000,-1364.5100000,16.8900000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.8500000,-1359.9600000,16.8900000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.8500000,-1359.9600000,21.1500000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.9600000,-1344.8600000,23.3400000,90.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.9600000,-1349.4100000,23.3400000,90.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.9600000,-1353.8100000,23.3400000,90.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.9600000,-1358.2100000,23.3400000,90.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.9600000,-1362.3300000,23.3400000,90.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.9600000,-1366.3000000,23.3400000,90.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.8500000,-1364.5100000,21.1500000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1173.0700000,-1367.3700000,23.2800000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.9600000,-1366.3000000,25.6100000,90.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.9600000,-1361.6200000,25.6100000,90.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.9600000,-1357.0700000,25.6100000,90.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.9600000,-1352.5300000,25.6100000,90.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.9600000,-1347.9800000,25.6100000,90.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(3440,1172.9600000,-1344.8600000,25.6100000,90.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19449,-207.3999939,-1739.6999512,676.5000000,0.0000000,0.0000000,0.0000000); //object number 0
	CreateDynamicObject(17038,-205.8994141,-1747.6992188,668.2999878,0.0000000,270.0000000,0.0000000); //object number 1
	CreateDynamicObject(17038,-204.3994141,-1747.6992188,668.2999878,0.0000000,270.0000000,0.0000000); //object number 2
	CreateDynamicObject(17038,-202.8999939,-1747.6999512,668.2999878,0.0000000,270.0000000,0.0000000); //object number 3
	CreateDynamicObject(17038,-201.3994141,-1747.6992188,668.2999878,0.0000000,270.0000000,0.0000000); //object number 4
	CreateDynamicObject(19460,-207.3990021,-1739.6999512,673.2999878,0.0000000,0.0000000,0.0000000); //object number 5
	CreateDynamicObject(19449,-202.5996094,-1734.7998047,676.5000000,0.0000000,0.0000000,90.0000000); //object number 6
	CreateDynamicObject(19460,-206.1999969,-1734.8010254,673.2999878,0.0000000,0.0000000,90.0000000); //object number 7
	CreateDynamicObject(1569,-206.0000000,-1734.9000244,674.7999878,0.0000000,0.0000000,0.0000000); //object number 8
	CreateDynamicObject(1569,-203.0000000,-1734.9000244,674.7999878,0.0000000,0.0000000,180.0000000); //object number 9
	CreateDynamicObject(19387,-196.6992188,-1744.5000000,676.5000000,0.0000000,0.0000000,90.0000000); //object number 10
	CreateDynamicObject(19357,-201.3994141,-1736.5000000,676.5000000,0.0000000,0.0000000,0.0000000); //object number 11
	CreateDynamicObject(19368,-201.4003906,-1736.5000000,673.2999878,0.0000000,0.0000000,0.0000000); //object number 12
	CreateDynamicObject(2885,-211.7998047,-1734.7998047,678.4000244,270.0000000,180.0000000,180.0000000); //object number 13
	CreateDynamicObject(17038,-199.8994141,-1747.6992188,668.2999878,0.0000000,270.0000000,0.0000000); //object number 14
	CreateDynamicObject(17038,-198.3999939,-1747.6999512,668.2999878,0.0000000,270.0000000,0.0000000); //object number 15
	CreateDynamicObject(17038,-196.8994141,-1747.6992188,668.2999878,0.0000000,270.0000000,0.0000000); //object number 16
	CreateDynamicObject(19449,-196.6000061,-1738.0159912,676.5000000,0.0000000,0.0000000,90.0000000); //object number 17
	CreateDynamicObject(19460,-196.6719971,-1738.0169678,673.2999878,0.0000000,0.0000000,90.0000000); //object number 18
	CreateDynamicObject(19449,-195.3994141,-1742.8994141,676.5000000,0.0000000,0.0000000,0.0000000); //object number 19
	CreateDynamicObject(17038,-195.3994141,-1747.6992188,668.2999878,0.0000000,270.0000000,0.0000000); //object number 20
	CreateDynamicObject(19460,-195.4010010,-1742.9000244,673.2999878,0.0000000,0.0000000,0.0000000); //object number 21
	CreateDynamicObject(19449,-201.1000061,-1739.6999512,674.0999756,0.0000000,0.0000000,0.0000000); //object number 22
	CreateDynamicObject(19460,-201.1005859,-1739.6992188,673.2999878,0.0000000,0.0000000,0.0000000); //object number 23
	CreateDynamicObject(19357,-199.8837891,-1744.5000000,676.5000000,0.0000000,0.0000000,90.0000000); //object number 24
	CreateDynamicObject(19460,-191.1503906,-1744.4990234,673.2999878,0.0000000,0.0000000,90.0000000); //object number 25
	CreateDynamicObject(19460,-191.1503906,-1744.5009766,673.2999878,0.0000000,0.0000000,90.0000000); //object number 26
	CreateDynamicObject(19368,-199.0749969,-1744.4990234,673.2999878,0.0000000,0.0000000,90.0000000); //object number 27
	CreateDynamicObject(19368,-199.0749969,-1744.5009766,673.2999878,0.0000000,0.0000000,90.0000000); //object number 28
	CreateDynamicObject(19368,-199.8849945,-1744.4980469,673.2999878,0.0000000,0.0000000,90.0000000); //object number 29
	CreateDynamicObject(19460,-201.0989990,-1739.5999756,673.2999878,0.0000000,0.0000000,0.0000000); //object number 30
	CreateDynamicObject(19357,-201.3994141,-1746.0996094,676.5000000,0.0000000,0.0000000,0.0000000); //object number 31
	CreateDynamicObject(19387,-201.3994141,-1749.2998047,676.5000000,0.0000000,0.0000000,0.0000000); //object number 32
	CreateDynamicObject(19357,-201.3999939,-1752.5000000,676.5000000,0.0000000,0.0000000,0.0000000); //object number 33
	CreateDynamicObject(19387,-201.3999939,-1755.6999512,676.5000000,0.0000000,0.0000000,0.0000000); //object number 34
	CreateDynamicObject(19357,-201.3994141,-1758.8994141,676.5000000,0.0000000,0.0000000,0.0000000); //object number 35
	CreateDynamicObject(17038,-205.8994141,-1768.3994141,668.2999878,0.0000000,270.0000000,0.0000000); //object number 36
	CreateDynamicObject(17038,-204.3994141,-1768.3994141,668.2999878,0.0000000,270.0000000,0.0000000); //object number 37
	CreateDynamicObject(17038,-202.8999939,-1768.4000244,668.2999878,0.0000000,270.0000000,0.0000000); //object number 38
	CreateDynamicObject(17038,-201.3999939,-1768.4000244,668.2999878,0.0000000,270.0000000,0.0000000); //object number 39
	CreateDynamicObject(17038,-199.8994141,-1768.3994141,668.2999878,0.0000000,270.0000000,0.0000000); //object number 40
	CreateDynamicObject(17038,-198.3994141,-1768.3994141,668.2999878,0.0000000,270.0000000,0.0000000); //object number 41
	CreateDynamicObject(17038,-196.8999939,-1768.4000244,668.2999878,0.0000000,270.0000000,0.0000000); //object number 42
	CreateDynamicObject(17038,-195.3994141,-1768.3994141,668.2999878,0.0000000,270.0000000,0.0000000); //object number 43
	CreateDynamicObject(19368,-201.4019928,-1746.0999756,673.2999878,0.0000000,0.0000000,0.0000000); //object number 44
	CreateDynamicObject(19368,-201.4010010,-1746.9250488,673.2999878,0.0000000,0.0000000,0.0000000); //object number 45
	CreateDynamicObject(19387,-201.3994141,-1762.0996094,676.5000000,0.0000000,0.0000000,0.0000000); //object number 46
	CreateDynamicObject(19368,-201.4010010,-1751.6369629,673.2999878,0.0000000,0.0000000,0.0000000); //object number 47
	CreateDynamicObject(19368,-201.4019928,-1753.3249512,673.2999878,0.0000000,0.0000000,0.0000000); //object number 48
	CreateDynamicObject(19368,-201.4010010,-1758.0369873,673.2999878,0.0000000,0.0000000,0.0000000); //object number 49
	CreateDynamicObject(19368,-201.4019928,-1759.7249756,673.2999878,0.0000000,0.0000000,0.0000000); //object number 50
	CreateDynamicObject(19387,-207.3994141,-1746.0996094,676.5000000,0.0000000,0.0000000,0.0000000); //object number 51
	CreateDynamicObject(19387,-207.3994141,-1758.8994141,676.5000000,0.0000000,0.0000000,0.0000000); //object number 52
	CreateDynamicObject(19357,-207.3994141,-1762.0996094,676.5000000,0.0000000,0.0000000,0.0000000); //object number 53
	CreateDynamicObject(19449,-195.3994141,-1752.5000000,676.5000000,0.0000000,0.0000000,0.0000000); //object number 54
	CreateDynamicObject(19449,-195.3994141,-1762.0996094,676.5000000,0.0000000,0.0000000,0.0000000); //object number 55
	CreateDynamicObject(19449,-196.5996094,-1758.7998047,676.5000000,0.0000000,0.0000000,90.0000000); //object number 56
	CreateDynamicObject(19460,-206.0000000,-1733.2998047,672.5999756,270.0000000,179.9945068,0.0000000); //object number 57
	CreateDynamicObject(19460,-203.0000000,-1733.3000488,672.5999756,270.0000000,179.9945068,0.0000000); //object number 58
	CreateDynamicObject(19441,-203.7140045,-1733.3010254,677.4000244,0.0000000,270.0000000,90.0000000); //object number 59
	CreateDynamicObject(19441,-205.2870026,-1733.3010254,677.4000244,0.0000000,270.0000000,90.0000000); //object number 60
	CreateDynamicObject(2885,-200.8994141,-1734.7998047,678.4000244,270.0000000,0.0000000,0.0000000); //object number 61
	CreateDynamicObject(2885,-200.8994141,-1741.5000000,678.4000244,270.0000000,0.0000000,0.0000000); //object number 62
	CreateDynamicObject(2885,-211.7998047,-1741.5000000,678.4000244,270.0000000,179.9945068,179.9945068); //object number 63
	CreateDynamicObject(2885,-211.7998047,-1748.1992188,678.4000244,270.0000000,0.0000000,0.0000000); //object number 64
	CreateDynamicObject(2885,-200.8999939,-1748.1999512,678.4000244,270.0000000,0.0000000,0.0000000); //object number 65
	CreateDynamicObject(2885,-200.8994141,-1754.8994141,678.4000244,270.0000000,0.0000000,0.0000000); //object number 66
	CreateDynamicObject(2885,-200.8994141,-1761.5996094,678.4000244,270.0000000,0.0000000,0.0000000); //object number 67
	CreateDynamicObject(2885,-211.7998047,-1761.5996094,678.4000244,270.0000000,0.0000000,0.0000000); //object number 68
	CreateDynamicObject(17038,-207.3994141,-1747.6992188,668.2999878,0.0000000,270.0000000,0.0000000); //object number 69
	CreateDynamicObject(17038,-208.8994141,-1747.6992188,668.2999878,0.0000000,270.0000000,0.0000000); //object number 70
	CreateDynamicObject(17038,-210.3999939,-1747.6999512,668.2999878,0.0000000,270.0000000,0.0000000); //object number 71
	CreateDynamicObject(17038,-211.8999939,-1747.6999512,668.2999878,0.0000000,270.0000000,0.0000000); //object number 72
	CreateDynamicObject(17038,-213.3994141,-1747.6992188,668.2999878,0.0000000,270.0000000,0.0000000); //object number 73
	CreateDynamicObject(17038,-213.3994141,-1768.3994141,668.2999878,0.0000000,270.0000000,0.0000000); //object number 74
	CreateDynamicObject(17038,-211.8999939,-1768.4000244,668.2999878,0.0000000,270.0000000,0.0000000); //object number 75
	CreateDynamicObject(17038,-210.3994141,-1768.3994141,668.2999878,0.0000000,270.0000000,0.0000000); //object number 76
	CreateDynamicObject(17038,-208.8994141,-1768.3994141,668.2999878,0.0000000,270.0000000,0.0000000); //object number 77
	CreateDynamicObject(17038,-207.3999939,-1768.4000244,668.2999878,0.0000000,270.0000000,0.0000000); //object number 78
	CreateDynamicObject(19449,-214.5996094,-1758.8994141,676.5000000,0.0000000,0.0000000,0.0000000); //object number 79
	CreateDynamicObject(19449,-214.5996094,-1749.2998047,676.5000000,0.0000000,0.0000000,0.0000000); //object number 80
	CreateDynamicObject(19449,-214.6000061,-1739.6999512,676.5000000,0.0000000,0.0000000,0.0000000); //object number 81
	CreateDynamicObject(19449,-212.1992188,-1734.7998047,676.5000000,0.0000000,0.0000000,90.0000000); //object number 82
	CreateDynamicObject(19368,-199.8000031,-1744.5010986,673.2999878,0.0000000,0.0000000,90.0000000); //object number 83
	CreateDynamicObject(19368,-201.3979950,-1746.0999756,673.2999878,0.0000000,0.0000000,0.0000000); //object number 84
	CreateDynamicObject(19368,-201.3990021,-1746.9250488,673.2999878,0.0000000,0.0000000,0.0000000); //object number 85
	CreateDynamicObject(19368,-201.3990021,-1751.6369629,673.2999878,0.0000000,0.0000000,0.0000000); //object number 86
	CreateDynamicObject(19368,-201.3970032,-1753.3242188,673.2999878,0.0000000,0.0000000,0.0000000); //object number 87
	CreateDynamicObject(19368,-201.3990021,-1758.0369873,673.2999878,0.0000000,0.0000000,0.0000000); //object number 88
	CreateDynamicObject(19368,-201.3979950,-1759.7249756,673.2999878,0.0000000,0.0000000,0.0000000); //object number 89
	CreateDynamicObject(19460,-195.4010010,-1752.5000000,673.2999878,0.0000000,0.0000000,0.0000000); //object number 90
	CreateDynamicObject(19460,-195.4003906,-1762.0996094,673.2999878,0.0000000,0.0000000,0.0000000); //object number 91
	CreateDynamicObject(19460,-196.6494141,-1758.7988281,673.2999878,0.0000000,0.0000000,90.0000000); //object number 92
	CreateDynamicObject(19460,-196.6494141,-1758.8007812,673.2999878,0.0000000,0.0000000,90.0000000); //object number 93
	CreateDynamicObject(19460,-207.3979950,-1740.5140381,673.2999878,0.0000000,0.0000000,0.0000000); //object number 94
	CreateDynamicObject(19368,-207.3984375,-1761.2363281,673.2999878,0.0000000,0.0000000,0.0000000); //object number 95
	CreateDynamicObject(19368,-207.3974609,-1764.3994141,673.2999878,0.0000000,0.0000000,0.0000000); //object number 96
	CreateDynamicObject(19460,-214.5986328,-1758.7998047,673.2999878,0.0000000,0.0000000,0.0000000); //object number 97
	CreateDynamicObject(19460,-214.5980072,-1749.1999512,673.2999878,0.0000000,0.0000000,0.0000000); //object number 98
	CreateDynamicObject(19460,-214.5989990,-1739.5999756,673.2999878,0.0000000,0.0000000,0.0000000); //object number 99
	CreateDynamicObject(19460,-215.8000031,-1734.8011475,673.2999878,0.0000000,0.0000000,90.0000000); //object number 100
	CreateDynamicObject(19460,-207.4010010,-1739.6999512,673.2999878,0.0000000,0.0000000,0.0000000); //object number 101
	CreateDynamicObject(19460,-207.4013672,-1740.5136719,673.2999878,0.0000000,0.0000000,0.0000000); //object number 102
	CreateDynamicObject(19368,-207.4011993,-1761.2370605,673.2999878,0.0000000,0.0000000,0.0000000); //object number 103
	CreateDynamicObject(19368,-207.4010010,-1764.3994141,673.2999878,0.0000000,0.0000000,0.0000000); //object number 104
	CreateDynamicObject(1523,-201.3699951,-1756.4499512,674.7399902,0.0000000,0.0000000,90.0000000); //object number 105
	CreateDynamicObject(1523,-201.3691406,-1750.0498047,674.7399902,0.0000000,0.0000000,90.0000000); //object number 106
	CreateDynamicObject(1523,-201.3691406,-1762.8496094,674.7399902,0.0000000,0.0000000,90.0000000); //object number 107
	CreateDynamicObject(2686,-201.5130005,-1744.9000244,676.4000244,0.0000000,0.0000000,270.0000000); //object number 108
	CreateDynamicObject(2685,-201.5130005,-1745.4000244,676.4000244,0.0000000,0.0000000,270.0000000); //object number 109
	CreateDynamicObject(2688,-207.2998047,-1747.5996094,676.2999878,0.0000000,0.0000000,90.0000000); //object number 110
	CreateDynamicObject(16101,-201.5000000,-1748.5000000,666.2999878,0.0000000,0.0000000,0.0000000); //object number 111
	CreateDynamicObject(16101,-201.5000000,-1750.0000000,666.2999878,0.0000000,0.0000000,0.0000000); //object number 112
	CreateDynamicObject(16101,-201.5000000,-1754.9000244,666.2999878,0.0000000,0.0000000,0.0000000); //object number 113
	CreateDynamicObject(16101,-201.5000000,-1756.4000244,666.2999878,0.0000000,0.0000000,0.0000000); //object number 114
	CreateDynamicObject(16101,-201.5000000,-1761.2998047,666.2999878,0.0000000,0.0000000,0.0000000); //object number 115
	CreateDynamicObject(16101,-201.5000000,-1762.8000488,666.2999878,0.0000000,0.0000000,0.0000000); //object number 116
	CreateDynamicObject(16101,-201.3291016,-1748.5000000,666.2999878,0.0000000,0.0000000,0.0000000); //object number 117
	CreateDynamicObject(16101,-201.3300018,-1750.0000000,666.2999878,0.0000000,0.0000000,0.0000000); //object number 118
	CreateDynamicObject(16101,-201.3300018,-1754.9000244,666.2999878,0.0000000,0.0000000,0.0000000); //object number 119
	CreateDynamicObject(16101,-201.3300018,-1756.4000244,666.2999878,0.0000000,0.0000000,0.0000000); //object number 120
	CreateDynamicObject(16101,-201.3300018,-1761.3000488,666.2999878,0.0000000,0.0000000,0.0000000); //object number 121
	CreateDynamicObject(16101,-201.3300018,-1762.8000488,666.2999878,0.0000000,0.0000000,0.0000000); //object number 122
	CreateDynamicObject(14487,-211.8000031,-1751.5000000,678.0999756,0.0000000,0.0000000,0.0000000); //object number 123
	CreateDynamicObject(14487,-211.7998047,-1729.5996094,678.0999756,0.0000000,0.0000000,0.0000000); //object number 124
	CreateDynamicObject(14487,-218.5996094,-1729.5996094,678.0999756,0.0000000,0.0000000,0.0000000); //object number 125
	CreateDynamicObject(14487,-218.6000061,-1754.3000488,678.0999756,0.0000000,0.0000000,0.0000000); //object number 126
	CreateDynamicObject(14487,-190.8994141,-1753.5996094,678.0999756,0.0000000,0.0000000,0.0000000); //object number 127
	CreateDynamicObject(14487,-190.8994141,-1735.1992188,678.0999756,0.0000000,0.0000000,0.0000000); //object number 128
	CreateDynamicObject(14487,-190.8994141,-1731.6992188,678.0999756,0.0000000,0.0000000,0.0000000); //object number 129
	CreateDynamicObject(1523,-207.3691406,-1746.8496094,674.7399902,0.0000000,0.0000000,90.0000000); //object number 130
	CreateDynamicObject(1523,-207.3691406,-1759.6494141,674.7399902,0.0000000,0.0000000,90.0000000); //object number 131
	CreateDynamicObject(16101,-207.3291016,-1745.2998047,666.2999878,0.0000000,0.0000000,0.0000000); //object number 132
	CreateDynamicObject(16101,-207.3300018,-1746.8199463,666.2999878,0.0000000,0.0000000,0.0000000); //object number 133
	CreateDynamicObject(16101,-207.3300018,-1758.0999756,666.2999878,0.0000000,0.0000000,0.0000000); //object number 134
	CreateDynamicObject(16101,-207.3291016,-1759.6191406,666.2999878,0.0000000,0.0000000,0.0000000); //object number 135
	CreateDynamicObject(16101,-207.5000000,-1759.5999756,666.2999878,0.0000000,0.0000000,0.0000000); //object number 136
	CreateDynamicObject(16101,-207.5000000,-1758.0999756,666.2999878,0.0000000,0.0000000,0.0000000); //object number 137
	CreateDynamicObject(16101,-207.5000000,-1746.8000488,666.2999878,0.0000000,0.0000000,0.0000000); //object number 138
	CreateDynamicObject(16101,-207.5000000,-1745.2998047,666.2999878,0.0000000,0.0000000,0.0000000); //object number 139
	CreateDynamicObject(1999,-200.5000000,-1740.3994141,674.7999878,0.0000000,0.0000000,90.0000000); //object number 140
	CreateDynamicObject(2009,-199.5000000,-1743.7998047,674.7999878,0.0000000,0.0000000,90.0000000); //object number 141
	CreateDynamicObject(1671,-199.5000000,-1739.3000488,675.2000122,0.0000000,0.0000000,270.0000000); //object number 142
	CreateDynamicObject(1671,-199.2998047,-1743.0000000,675.2000122,0.0000000,0.0000000,270.0000000); //object number 143
	CreateDynamicObject(19387,-213.0000000,-1742.6992188,676.5000000,0.0000000,0.0000000,90.0000000); //object number 144
	CreateDynamicObject(19357,-209.7998047,-1742.6992188,673.9010010,0.0000000,0.0000000,90.0000000); //object number 145
	CreateDynamicObject(19357,-209.0000000,-1742.7001953,673.9000244,0.0000000,0.0000000,90.0000000); //object number 146
	CreateDynamicObject(19449,-212.1999969,-1742.6989746,679.0000000,0.0000000,0.0000000,90.0000000); //object number 147
	CreateDynamicObject(19466,-208.5000000,-1742.6999512,676.4000244,0.0000000,0.0000000,90.0000000); //object number 148
	CreateDynamicObject(19466,-210.7402344,-1742.6992188,676.4000244,0.0000000,0.0000000,90.0000000); //object number 149
	CreateDynamicObject(19368,-209.0000000,-1742.6989746,673.2999878,0.0000000,0.0000000,90.0000000); //object number 150
	CreateDynamicObject(19368,-210.6640015,-1742.6979980,673.2999878,0.0000000,0.0000000,90.0000000); //object number 151
	CreateDynamicObject(19368,-215.3739929,-1742.6989746,673.2999878,0.0000000,0.0000000,90.0000000); //object number 152
	CreateDynamicObject(19368,-215.3750000,-1742.7001953,673.2999878,0.0000000,0.0000000,90.0000000); //object number 153
	CreateDynamicObject(19368,-209.0000000,-1742.7011719,673.2999878,0.0000000,0.0000000,90.0000000); //object number 154
	CreateDynamicObject(19368,-210.6640015,-1742.7021484,673.2999878,0.0000000,0.0000000,90.0000000); //object number 155
	CreateDynamicObject(1523,-213.7890625,-1742.7294922,674.7399902,0.0000000,0.0000000,0.0000000); //object number 156
	CreateDynamicObject(16101,-212.2998047,-1742.7998047,666.2999878,0.0000000,0.0000000,0.0000000); //object number 157
	CreateDynamicObject(16101,-213.8000031,-1742.8000488,666.2999878,0.0000000,0.0000000,0.0000000); //object number 158
	CreateDynamicObject(16101,-213.8000031,-1742.5999756,666.2999878,0.0000000,0.0000000,0.0000000); //object number 159
	CreateDynamicObject(16101,-212.3000031,-1742.5999756,666.2999878,0.0000000,0.0000000,0.0000000); //object number 160
	CreateDynamicObject(16101,-207.5000000,-1742.6992188,666.9000244,0.0000000,0.0000000,0.0000000); //object number 161
	CreateDynamicObject(3657,-213.8999939,-1745.6999512,675.2999878,0.0000000,0.0000000,90.0000000); //object number 162
	CreateDynamicObject(3394,-213.7998047,-1739.0000000,674.7999878,0.0000000,0.0000000,179.9945068); //object number 163
	CreateDynamicObject(3396,-208.1992188,-1737.0000000,674.7999878,0.0000000,0.0000000,0.0000000); //object number 164
	CreateDynamicObject(3397,-208.1992188,-1740.8994141,674.7999878,0.0000000,0.0000000,0.0000000); //object number 165
	CreateDynamicObject(14487,-218.6000061,-1731.8000488,678.0999756,0.0000000,0.0000000,0.0000000); //object number 166
	CreateDynamicObject(2007,-213.6992188,-1735.3994141,674.7999878,0.0000000,0.0000000,0.0000000); //object number 167
	CreateDynamicObject(2007,-212.6992188,-1735.3994141,674.7999878,0.0000000,0.0000000,0.0000000); //object number 168
	CreateDynamicObject(2132,-211.0996094,-1735.3994141,674.7999878,0.0000000,0.0000000,0.0000000); //object number 169
	CreateDynamicObject(14532,-211.3994141,-1737.0996094,675.7800293,0.0000000,0.0000000,194.7491455); //object number 170
	CreateDynamicObject(2146,-211.0996094,-1738.7998047,675.2700195,0.0000000,0.0000000,0.0000000); //object number 171
	CreateDynamicObject(3657,-206.8999939,-1754.5999756,675.2999878,0.0000000,0.0000000,90.0000000); //object number 172
	CreateDynamicObject(2811,-201.8994141,-1735.3994141,674.7999878,0.0000000,0.0000000,139.9932861); //object number 173
	CreateDynamicObject(2811,-201.8999939,-1763.1999512,674.7999878,0.0000000,0.0000000,219.9957275); //object number 174
	CreateDynamicObject(2811,-206.8994141,-1763.1992188,674.7999878,0.0000000,0.0000000,149.9908752); //object number 175
	CreateDynamicObject(3657,-206.8999939,-1739.5999756,675.2999878,0.0000000,0.0000000,90.0000000); //object number 176
	CreateDynamicObject(2811,-206.8994141,-1735.3994141,674.7999878,0.0000000,0.0000000,221.9897461); //object number 177
	CreateDynamicObject(2688,-201.5000000,-1760.5000000,676.4000244,0.0000000,0.0000000,270.0000000); //object number 178
	CreateDynamicObject(19460,-201.5000000,-1739.6999512,679.9000244,0.0000000,179.9945068,0.0000000); //object number 179
	CreateDynamicObject(19460,-207.3000031,-1739.6999512,679.9000244,0.0000000,179.9945068,0.0000000); //object number 180
	CreateDynamicObject(19460,-207.3000031,-1749.3000488,679.9000244,0.0000000,179.9945068,0.0000000); //object number 181
	CreateDynamicObject(19460,-207.2998047,-1758.8994141,679.9000244,0.0000000,179.9945068,0.0000000); //object number 182
	CreateDynamicObject(19460,-201.5000000,-1749.3000488,679.9000244,0.0000000,179.9945068,0.0000000); //object number 183
	CreateDynamicObject(19460,-201.5000000,-1758.8994141,679.9000244,0.0000000,179.9945068,0.0000000); //object number 184
	CreateDynamicObject(19460,-204.8000031,-1734.9000244,679.9000244,0.0000000,179.9945068,90.0000000); //object number 185
	CreateDynamicObject(19460,-214.5000000,-1758.9000244,679.9000244,0.0000000,179.9945068,0.0000000); //object number 186
	CreateDynamicObject(19460,-214.5000000,-1749.3000488,679.9000244,0.0000000,179.9945068,0.0000000); //object number 187
	CreateDynamicObject(19460,-214.5000000,-1739.6999512,679.9000244,0.0000000,179.9945068,0.0000000); //object number 188
	CreateDynamicObject(19460,-207.5000000,-1758.9000244,679.9000244,0.0000000,179.9945068,0.0000000); //object number 189
	CreateDynamicObject(19460,-207.5000000,-1749.3000488,679.9000244,0.0000000,179.9945068,0.0000000); //object number 190
	CreateDynamicObject(19460,-207.5000000,-1739.6999512,679.9000244,0.0000000,179.9945068,0.0000000); //object number 191
	CreateDynamicObject(19460,-214.3999939,-1734.9000244,679.9000244,0.0000000,179.9945068,90.0000000); //object number 192
	CreateDynamicObject(19460,-212.1999969,-1742.8000488,679.9000244,0.0000000,179.9945068,90.0000000); //object number 193
	CreateDynamicObject(19460,-212.1999969,-1742.5999756,679.9000244,0.0000000,179.9945068,90.0000000); //object number 194
	CreateDynamicObject(19460,-196.6000061,-1744.4000244,679.9000244,0.0000000,179.9945068,90.0000000); //object number 195
	CreateDynamicObject(19460,-196.6000061,-1738.0999756,679.9000244,0.0000000,179.9945068,90.0000000); //object number 196
	CreateDynamicObject(19460,-196.6000061,-1744.5999756,679.9000244,0.0000000,179.9945068,90.0000000); //object number 197
	CreateDynamicObject(19460,-196.6000061,-1758.6999512,679.9000244,0.0000000,179.9945068,90.0000000); //object number 198
	CreateDynamicObject(19460,-196.6000061,-1758.9000244,679.9000244,0.0000000,179.9945068,90.0000000); //object number 199
	CreateDynamicObject(19460,-195.5000000,-1758.9000244,679.9000244,0.0000000,179.9945068,0.0000000); //object number 200
	CreateDynamicObject(19460,-195.5000000,-1749.3000488,679.9000244,0.0000000,179.9945068,0.0000000); //object number 201
	CreateDynamicObject(19460,-195.5000000,-1739.6999512,679.9000244,0.0000000,179.9945068,0.0000000); //object number 202
	CreateDynamicObject(19357,-209.0000000,-1748.8010254,673.9010010,0.0000000,0.0000000,90.0000000); //object number 203
	CreateDynamicObject(19449,-207.3999939,-1752.5000000,676.5000000,0.0000000,0.0000000,0.0000000); //object number 204
	CreateDynamicObject(19460,-207.4010010,-1751.5999756,673.2999878,0.0000000,0.0000000,0.0000000); //object number 205
	CreateDynamicObject(19460,-207.3990021,-1751.5999756,673.2999878,0.0000000,0.0000000,0.0000000); //object number 206
	CreateDynamicObject(19460,-207.4019928,-1753.3000488,673.2999878,0.0000000,0.0000000,0.0000000); //object number 207
	CreateDynamicObject(19460,-207.3979950,-1753.3000488,673.2999878,0.0000000,0.0000000,0.0000000); //object number 208
	CreateDynamicObject(3657,-206.8999939,-1750.4000244,675.2999878,0.0000000,0.0000000,90.0000000); //object number 209
	CreateDynamicObject(19387,-213.0000000,-1748.8000488,676.5000000,0.0000000,0.0000000,90.0000000); //object number 210
	CreateDynamicObject(19449,-212.1999969,-1748.8010254,679.0000000,0.0000000,0.0000000,90.0000000); //object number 211
	CreateDynamicObject(19357,-209.8000031,-1748.8000488,673.9000244,0.0000000,0.0000000,90.0000000); //object number 212
	CreateDynamicObject(19466,-208.6000061,-1748.8000488,676.4000244,0.0000000,0.0000000,90.0000000); //object number 213
	CreateDynamicObject(19466,-210.8398438,-1748.7998047,676.4000244,0.0000000,0.0000000,90.0000000); //object number 214
	CreateDynamicObject(19449,-212.1999969,-1756.1999512,676.5000000,0.0000000,0.0000000,90.0000000); //object number 215
	CreateDynamicObject(1523,-213.7890015,-1748.8299561,674.7399902,0.0000000,0.0000000,0.0000000); //object number 216
	CreateDynamicObject(19460,-212.1999969,-1748.6999512,679.9000244,0.0000000,179.9945068,90.0000000); //object number 217
	CreateDynamicObject(19460,-212.1999969,-1748.9000244,679.9000244,0.0000000,179.9945068,90.0000000); //object number 218
	CreateDynamicObject(19460,-212.1999969,-1756.0999756,679.9000244,0.0000000,179.9945068,90.0000000); //object number 219
	CreateDynamicObject(19460,-212.3000031,-1756.1989746,673.2999878,0.0000000,0.0000000,90.0000000); //object number 220
	CreateDynamicObject(19368,-209.0000000,-1748.7989502,673.2999878,0.0000000,0.0000000,90.0000000); //object number 221
	CreateDynamicObject(19368,-210.6629944,-1748.7989502,673.2999878,0.0000000,0.0000000,90.0000000); //object number 222
	CreateDynamicObject(19368,-210.6621094,-1748.8027344,673.2999878,0.0000000,0.0000000,90.0000000); //object number 223
	CreateDynamicObject(19368,-209.0000000,-1748.8017578,673.2999878,0.0000000,0.0000000,90.0000000); //object number 224
	CreateDynamicObject(19368,-215.3750000,-1748.7989502,673.2999878,0.0000000,0.0000000,90.0000000); //object number 225
	CreateDynamicObject(19368,-215.3750000,-1748.8007812,673.2999878,0.0000000,0.0000000,90.0000000); //object number 226
	CreateDynamicObject(3397,-208.1999969,-1750.8000488,674.7999878,0.0000000,0.0000000,0.0000000); //object number 227
	CreateDynamicObject(3396,-208.1999969,-1754.4000244,674.7999878,0.0000000,0.0000000,0.0000000); //object number 228
	CreateDynamicObject(19460,-212.1999969,-1756.3000488,679.9000244,0.0000000,179.9945068,90.0000000); //object number 229
	CreateDynamicObject(2132,-209.8999939,-1755.5999756,674.7999878,0.0000000,0.0000000,180.0000000); //object number 230
	CreateDynamicObject(2007,-212.3000031,-1755.5999756,674.7999878,0.0000000,0.0000000,180.0000000); //object number 231
	CreateDynamicObject(2007,-213.3000031,-1755.5999756,674.7999878,0.0000000,0.0000000,179.9945068); //object number 232
	CreateDynamicObject(3394,-213.8000031,-1752.1999512,674.7999878,0.0000000,0.0000000,179.9945068); //object number 233
	CreateDynamicObject(2146,-211.1000061,-1751.9000244,675.2999878,0.0000000,0.0000000,0.0000000); //object number 234
	CreateDynamicObject(14532,-210.6999969,-1753.5000000,675.7999878,0.0000000,0.0000000,14.0000000); //object number 235
	CreateDynamicObject(19460,-212.2998047,-1756.2001953,673.2999878,0.0000000,0.0000000,90.0000000); //object number 236
	CreateDynamicObject(3657,-201.8994141,-1746.5000000,675.2999878,0.0000000,0.0000000,270.0000000); //object number 237
	CreateDynamicObject(2811,-214.0000000,-1743.4000244,674.7999878,0.0000000,0.0000000,251.9897461); //object number 238
	CreateDynamicObject(2811,-214.0000000,-1748.0999756,674.7999878,0.0000000,0.0000000,295.9879761); //object number 239
	CreateDynamicObject(16101,-207.5000000,-1748.8000488,666.9000244,0.0000000,0.0000000,0.0000000); //object number 240
	CreateDynamicObject(3394,-213.7998047,-1761.5000000,674.7999878,0.0000000,0.0000000,179.9945068); //object number 241
	CreateDynamicObject(2007,-214.0000000,-1758.5999756,674.7999878,0.0000000,0.0000000,90.0000000); //object number 242
	CreateDynamicObject(2007,-214.0000000,-1757.5999756,674.7999878,0.0000000,0.0000000,90.0000000); //object number 243
	CreateDynamicObject(2132,-210.1000061,-1763.0999756,674.7999878,0.0000000,0.0000000,179.9945068); //object number 244
	CreateDynamicObject(3396,-208.1999969,-1761.6999512,674.7999878,0.0000000,0.0000000,0.0000000); //object number 245
	CreateDynamicObject(3397,-210.8000031,-1756.6999512,674.7999878,0.0000000,0.0000000,90.0000000); //object number 246
	CreateDynamicObject(2146,-211.1999969,-1759.9000244,675.2999878,0.0000000,0.0000000,0.0000000); //object number 247
	CreateDynamicObject(11237,-230.0000000,-1760.3994141,698.9000244,0.0000000,179.9945068,179.9945068); //object number 248
	CreateDynamicObject(3053,-211.1999969,-1760.4000244,678.4000244,0.0000000,0.0000000,0.0000000); //object number 249
	CreateDynamicObject(16101,-211.1999969,-1760.4000244,688.0999756,0.0000000,180.0000000,0.0000000); //object number 250
	CreateDynamicObject(2596,-214.3000031,-1760.0999756,676.7000122,0.0000000,0.0000000,90.0000000); //object number 251
	CreateDynamicObject(2885,-211.8000031,-1754.9000244,678.4000244,270.0000000,0.0000000,0.0000000); //object number 252
	CreateDynamicObject(2596,-214.3000031,-1760.8000488,676.7000122,0.0000000,0.0000000,90.0000000); //object number 253
	CreateDynamicObject(2596,-214.3000031,-1760.8000488,677.2999878,0.0000000,0.0000000,90.0000000); //object number 254
	CreateDynamicObject(2596,-214.3000031,-1760.0999756,677.2999878,0.0000000,0.0000000,90.0000000); //object number 255
	CreateDynamicObject(16101,-222.5996094,-1760.3994141,677.9000244,0.0000000,90.0000000,0.0000000); //object number 256
	CreateDynamicObject(16101,-214.5000000,-1760.4000244,666.1938722,0.0000000,0.0000000,0.0000000); //object number 257
	CreateDynamicObject(3808,-207.2500000,-1757.7998047,676.2999878,0.0000000,0.0000000,0.0000000); //object number 258
	CreateDynamicObject(3808,-212.0000000,-1742.8499756,676.2999878,0.0000000,0.0000000,270.0000000); //object number 259
	CreateDynamicObject(3808,-212.0000000,-1748.6600342,676.2999878,0.0000000,0.0000000,90.0000000); //object number 260
	CreateDynamicObject(19460,-201.3000031,-1749.5000000,679.9000244,0.0000000,179.9945068,0.0000000); //object number 261
	CreateDynamicObject(19460,-201.3000031,-1759.0999756,679.9000244,0.0000000,179.9945068,0.0000000); //object number 262
	CreateDynamicObject(2009,-199.5000000,-1747.8000488,674.7999878,0.0000000,0.0000000,90.0000000); //object number 263
	CreateDynamicObject(1999,-200.5000000,-1746.0999756,674.8010254,0.0000000,0.0000000,90.0000000); //object number 264
	CreateDynamicObject(1671,-199.3999939,-1746.9000244,675.2000122,0.0000000,0.0000000,264.0000000); //object number 265
	CreateDynamicObject(1671,-199.3999939,-1745.0999756,675.2000122,0.0000000,0.0000000,278.0000000); //object number 266
	CreateDynamicObject(2009,-196.8000031,-1753.8000488,674.8010254,0.0000000,0.0000000,90.0000000); //object number 267
	CreateDynamicObject(1999,-197.8000031,-1752.0999756,674.7999878,0.0000000,0.0000000,90.0000000); //object number 268
	CreateDynamicObject(1999,-198.6999969,-1752.8000488,674.7999878,0.0000000,0.0000000,270.0000000); //object number 269
	CreateDynamicObject(2009,-199.6999969,-1751.0999756,674.8010254,0.0000000,0.0000000,270.0000000); //object number 270
	CreateDynamicObject(1671,-197.6000061,-1753.0000000,675.2000122,0.0000000,0.0000000,282.0000000); //object number 271
	CreateDynamicObject(1671,-196.8000031,-1751.3000488,675.2000122,0.0000000,0.0000000,260.0000000); //object number 272
	CreateDynamicObject(1671,-199.8000031,-1752.0999756,675.2000122,0.0000000,0.0000000,84.0000000); //object number 273
	CreateDynamicObject(1671,-199.8000031,-1753.8000488,675.2000122,0.0000000,0.0000000,104.0000000); //object number 274
	CreateDynamicObject(2009,-196.0000000,-1757.1999512,674.7999878,0.0000000,0.0000000,180.0000000); //object number 275
	CreateDynamicObject(1999,-197.6999969,-1758.1999512,674.8010254,0.0000000,0.0000000,180.0000000); //object number 276
	CreateDynamicObject(1671,-196.8999939,-1757.3000488,675.2000122,0.0000000,0.0000000,0.0000000); //object number 277
	CreateDynamicObject(1671,-198.6999969,-1758.0000000,675.2000122,0.0000000,0.0000000,0.0000000); //object number 278
	CreateDynamicObject(2202,-196.0000000,-1746.1999512,674.7800293,0.0000000,0.0000000,270.0000000); //object number 279
	CreateDynamicObject(2811,-195.8999939,-1745.0999756,674.7999878,0.0000000,0.0000000,115.9932861); //object number 280
	CreateDynamicObject(2007,-196.0000000,-1748.3000488,674.7999878,0.0000000,0.0000000,270.0000000); //object number 281
	CreateDynamicObject(2007,-196.0000000,-1749.3000488,674.7999878,0.0000000,0.0000000,270.0000000); //object number 282
	CreateDynamicObject(2811,-200.8999939,-1758.3000488,674.7999878,0.0000000,0.0000000,141.9881592); //object number 283
	CreateDynamicObject(2611,-198.1999969,-1758.6700439,676.7999878,0.0000000,0.0000000,180.0000000); //object number 284
	CreateDynamicObject(2611,-201.2700043,-1746.4000244,676.5999756,0.0000000,0.0000000,89.9945068); //object number 288
	CreateDynamicObject(19449,-212.1999969,-1763.6999512,676.5000000,0.0000000,0.0000000,90.0000000); //object number 289
	CreateDynamicObject(19449,-195.3994141,-1771.6992188,676.5000000,0.0000000,0.0000000,0.0000000); //object number 290
	CreateDynamicObject(2885,-200.8994141,-1768.2998047,678.4000244,270.0000000,180.0000000,180.0000000); //object number 291
	CreateDynamicObject(19460,-201.3984375,-1767.5791016,673.3010254,0.0000000,0.0000000,0.0000000); //object number 292
	CreateDynamicObject(19460,-195.4003906,-1771.6992188,673.2999878,0.0000000,0.0000000,0.0000000); //object number 293
	CreateDynamicObject(19460,-195.5000000,-1768.5000000,679.9000244,0.0000000,179.9945068,0.0000000); //object number 294
	CreateDynamicObject(19460,-201.2998047,-1768.6992188,679.9000244,0.0000000,179.9945068,0.0000000); //object number 295
	CreateDynamicObject(14487,-190.8994141,-1778.1992188,678.0999756,0.0000000,0.0000000,0.0000000); //object number 296
	CreateDynamicObject(1789,-211.8000031,-1753.0999756,675.2999878,0.0000000,0.0000000,290.0000000); //object number 297
	CreateDynamicObject(1789,-211.8994141,-1759.1992188,675.2999878,0.0000000,0.0000000,270.0000000); //object number 298
	CreateDynamicObject(1789,-210.1999969,-1737.6999512,675.2999878,0.0000000,0.0000000,99.9951172); //object number 299
	CreateDynamicObject(19460,-212.1999969,-1763.5999756,679.9000244,0.0000000,179.9945068,90.0000000); //object number 300
	CreateDynamicObject(1999,-197.5000000,-1740.4000244,674.7999878,0.0000000,0.0000000,90.0000000); //object number 301
	CreateDynamicObject(1671,-196.5000000,-1739.3000488,675.2000122,0.0000000,0.0000000,270.0000000); //object number 302
	CreateDynamicObject(19460,-212.3000031,-1765.4010010,673.2999878,0.0000000,0.0000000,90.0000000); //object number 305
	CreateDynamicObject(16101,-212.3000031,-1748.6999512,666.2999878,0.0000000,0.0000000,0.0000000); //object number 306
	CreateDynamicObject(16101,-213.8000031,-1748.6999512,666.2999878,0.0000000,0.0000000,0.0000000); //object number 307
	CreateDynamicObject(16101,-213.8000031,-1748.9000244,666.2999878,0.0000000,0.0000000,0.0000000); //object number 308
	CreateDynamicObject(16101,-212.3000031,-1748.9000244,666.2999878,0.0000000,0.0000000,0.0000000); //object number 309
	CreateDynamicObject(2852,-206.8000031,-1742.8000488,675.2800293,0.0000000,0.0000000,0.0000000); //object number 310
	CreateDynamicObject(2315,-206.8000031,-1742.4000244,674.7999878,0.0000000,0.0000000,270.0000000); //object number 311
	CreateDynamicObject(2855,-206.6999969,-1743.6999512,675.2999878,0.0000000,0.0000000,0.0000000); //object number 312
	CreateDynamicObject(19387,-207.3994141,-1768.5000000,676.5000000,0.0000000,0.0000000,0.0000000); //object number 313
	CreateDynamicObject(19357,-207.3994141,-1765.2998047,676.5000000,0.0000000,0.0000000,0.0000000); //object number 314
	CreateDynamicObject(19387,-207.3994141,-1773.2998047,676.5000000,0.0000000,0.0000000,0.0000000); //object number 315
	CreateDynamicObject(17038,-213.3999939,-1789.0999756,668.2999878,0.0000000,270.0000000,0.0000000); //object number 316
	CreateDynamicObject(17038,-211.8994141,-1789.0996094,668.2999878,0.0000000,270.0000000,0.0000000); //object number 317
	CreateDynamicObject(17038,-210.3999939,-1789.0999756,668.2999878,0.0000000,270.0000000,0.0000000); //object number 318
	CreateDynamicObject(17038,-208.8999939,-1789.0999756,668.2999878,0.0000000,270.0000000,0.0000000); //object number 319
	CreateDynamicObject(17038,-207.3999939,-1789.0999756,668.2999878,0.0000000,270.0000000,0.0000000); //object number 320
	CreateDynamicObject(17038,-205.8999939,-1789.0999756,668.2999878,0.0000000,270.0000000,0.0000000); //object number 321
	CreateDynamicObject(17038,-204.3999939,-1789.0999756,668.2999878,0.0000000,270.0000000,0.0000000); //object number 322
	CreateDynamicObject(17038,-202.8999939,-1789.0999756,668.2999878,0.0000000,270.0000000,0.0000000); //object number 323
	CreateDynamicObject(17038,-201.3994141,-1789.0996094,668.2999878,0.0000000,270.0000000,0.0000000); //object number 324
	CreateDynamicObject(17038,-199.8994141,-1789.0996094,668.2999878,0.0000000,270.0000000,0.0000000); //object number 325
	CreateDynamicObject(17038,-198.3999939,-1789.0999756,668.2999878,0.0000000,270.0000000,0.0000000); //object number 326
	CreateDynamicObject(17038,-196.8994141,-1789.0996094,668.2999878,0.0000000,270.0000000,0.0000000); //object number 327
	CreateDynamicObject(17038,-195.3999939,-1789.0999756,668.2999878,0.0000000,270.0000000,0.0000000); //object number 328
	CreateDynamicObject(19449,-212.1269989,-1779.6999512,676.5000000,0.0000000,0.0000000,90.0000000); //object number 329
	CreateDynamicObject(19449,-214.5996094,-1768.5000000,676.5000000,0.0000000,0.0000000,0.0000000); //object number 330
	CreateDynamicObject(19449,-214.6000061,-1778.0999756,676.5000000,0.0000000,0.0000000,0.0000000); //object number 331
	CreateDynamicObject(19449,-214.6000061,-1787.6999512,676.5000000,0.0000000,0.0000000,0.0000000); //object number 332
	CreateDynamicObject(19387,-213.0000000,-1785.1992188,676.5000000,0.0000000,0.0000000,270.0000000); //object number 333
	CreateDynamicObject(19387,-207.0000000,-1785.1999512,676.5000000,0.0000000,0.0000000,270.0000000); //object number 334
	CreateDynamicObject(19430,-210.5996094,-1785.1992188,676.5000000,0.0000000,0.0000000,270.0000000); //object number 335
	CreateDynamicObject(19387,-201.8000031,-1785.1999512,676.5000000,0.0000000,0.0000000,270.0000000); //object number 336
	CreateDynamicObject(19430,-199.3994141,-1785.1992188,676.5000000,0.0000000,0.0000000,90.0000000); //object number 337
	CreateDynamicObject(19387,-197.0000000,-1785.1992188,676.5000000,0.0000000,0.0000000,270.0000000); //object number 338
	CreateDynamicObject(19449,-195.3994141,-1781.2998047,676.5000000,0.0000000,0.0000000,0.0000000); //object number 339
	CreateDynamicObject(19449,-209.8000031,-1790.0000000,676.5000000,0.0000000,0.0000000,0.0000000); //object number 340
	CreateDynamicObject(19449,-204.3999939,-1790.0000000,676.5000000,0.0000000,0.0000000,0.0000000); //object number 341
	CreateDynamicObject(19449,-200.1999969,-1790.0000000,676.5000000,0.0000000,0.0000000,0.0000000); //object number 342
	CreateDynamicObject(19449,-195.3999939,-1790.9000244,676.5000000,0.0000000,0.0000000,0.0000000); //object number 343
	CreateDynamicObject(19449,-200.1999969,-1792.1999512,676.5000000,0.0000000,0.0000000,90.0000000); //object number 344
	CreateDynamicObject(19449,-209.7998047,-1792.1992188,676.5000000,0.0000000,0.0000000,90.0000000); //object number 345
	CreateDynamicObject(19430,-207.3994141,-1770.8994141,676.5000000,0.0000000,0.0000000,179.9945068); //object number 346
	CreateDynamicObject(19387,-207.3994141,-1776.5000000,676.5000000,0.0000000,0.0000000,0.0000000); //object number 347
	CreateDynamicObject(19449,-212.1999969,-1775.0000000,676.5000000,0.0000000,0.0000000,90.0000000); //object number 348
	CreateDynamicObject(19449,-212.1999969,-1770.1999512,676.5000000,0.0000000,0.0000000,90.0000000); //object number 349
	CreateDynamicObject(19449,-212.1992188,-1765.3994141,676.5000000,0.0000000,0.0000000,90.0000000); //object number 350
	CreateDynamicObject(19460,-195.4004059,-1781.3000488,673.2999878,0.0000000,0.0000000,0.0000000); //object number 351
	CreateDynamicObject(19460,-195.4004059,-1790.9000244,673.2999878,0.0000000,0.0000000,0.0000000); //object number 352
	CreateDynamicObject(19460,-214.5980072,-1768.4000244,673.2999878,0.0000000,0.0000000,0.0000000); //object number 353
	CreateDynamicObject(19460,-214.5980072,-1778.0000000,673.2999878,0.0000000,0.0000000,0.0000000); //object number 354
	CreateDynamicObject(19460,-214.5980072,-1787.5996094,673.2999878,0.0000000,0.0000000,0.0000000); //object number 355
	CreateDynamicObject(19460,-212.3000031,-1763.6979980,673.2999878,0.0000000,0.0000000,90.0000000); //object number 356
	CreateDynamicObject(19460,-212.3000031,-1770.2010498,673.2999878,0.0000000,0.0000000,90.0000000); //object number 357
	CreateDynamicObject(19460,-212.2998047,-1770.1972656,673.2999878,0.0000000,0.0000000,90.0000000); //object number 358
	CreateDynamicObject(19460,-212.3000031,-1774.9980469,673.2999878,0.0000000,0.0000000,90.0000000); //object number 359
	CreateDynamicObject(19460,-212.3000031,-1775.0009766,673.2999878,0.0000000,0.0000000,90.0000000); //object number 360
	CreateDynamicObject(19460,-212.3000031,-1779.6979980,673.2999878,0.0000000,0.0000000,90.0000000); //object number 361
	CreateDynamicObject(19460,-212.2998047,-1779.7001953,673.2999878,0.0000000,0.0000000,90.0000000); //object number 362
	CreateDynamicObject(19368,-207.3981018,-1766.1250000,673.2999878,0.0000000,0.0000000,0.0000000); //object number 363
	CreateDynamicObject(19368,-207.4015045,-1766.1250000,673.2999878,0.0000000,0.0000000,0.0000000); //object number 364
	CreateDynamicObject(19368,-207.4010010,-1770.8360596,673.2999878,0.0000000,0.0000000,0.0000000); //object number 365
	CreateDynamicObject(19368,-207.4015045,-1770.9260254,673.2999878,0.0000000,0.0000000,0.0000000); //object number 366
	CreateDynamicObject(19368,-207.3974609,-1770.9248047,673.2999878,0.0000000,0.0000000,0.0000000); //object number 367
	CreateDynamicObject(19368,-207.3984985,-1770.8360596,673.2999878,0.0000000,0.0000000,0.0000000); //object number 368
	CreateDynamicObject(19441,-207.3979950,-1774.8344727,673.2999878,0.0000000,0.0000000,0.0000000); //object number 369
	CreateDynamicObject(19441,-207.4010010,-1774.8339844,673.2999878,0.0000000,0.0000000,0.0000000); //object number 370
	CreateDynamicObject(19441,-207.4015045,-1774.9279785,673.2999878,0.0000000,0.0000000,0.0000000); //object number 371
	CreateDynamicObject(19441,-207.3979950,-1774.9279785,673.2999878,0.0000000,0.0000000,0.0000000); //object number 372
	CreateDynamicObject(19441,-207.3974609,-1778.0332031,673.2999878,0.0000000,0.0000000,0.0000000); //object number 373
	CreateDynamicObject(19441,-207.3970032,-1778.9899902,673.2999878,0.0000000,0.0000000,0.0000000); //object number 374
	CreateDynamicObject(19441,-207.4010010,-1778.9000244,673.2999878,0.0000000,0.0000000,0.0000000); //object number 375
	CreateDynamicObject(19441,-207.4015045,-1778.0340576,673.2999878,0.0000000,0.0000000,0.0000000); //object number 376
	CreateDynamicObject(19430,-207.3999939,-1778.9000244,676.5000000,0.0000000,0.0000000,180.0000000); //object number 377
	CreateDynamicObject(19460,-201.4010010,-1767.5999756,673.2999878,0.0000000,0.0000000,0.0000000); //object number 378
	CreateDynamicObject(19460,-196.6000061,-1779.6979980,673.3010254,0.0000000,0.0000000,90.0000000); //object number 379
	CreateDynamicObject(19368,-201.3999939,-1778.0000000,673.2999878,0.0000000,0.0000000,0.0000000); //object number 380
	CreateDynamicObject(19460,-207.3000031,-1768.5000000,679.9000244,0.0000000,179.9945068,0.0000000); //object number 381
	CreateDynamicObject(19460,-207.3000031,-1778.0999756,679.9000244,0.0000000,179.9945068,0.0000000); //object number 382
	CreateDynamicObject(19460,-201.5000000,-1768.5000000,679.9000244,0.0000000,179.9945068,0.0000000); //object number 383
	CreateDynamicObject(19460,-201.5000000,-1778.0999756,679.9000244,0.0000000,179.9945068,0.0000000); //object number 384
	CreateDynamicObject(19460,-207.5000000,-1768.5000000,679.9000244,0.0000000,179.9945068,0.0000000); //object number 385
	CreateDynamicObject(19460,-207.5010071,-1774.9000244,679.9000244,0.0000000,179.9945068,0.0000000); //object number 386
	CreateDynamicObject(19460,-201.3009949,-1774.9000244,679.9000244,0.0000000,179.9945068,0.0000000); //object number 387
	CreateDynamicObject(19460,-196.6000061,-1779.5999756,679.9000244,0.0000000,179.9945068,90.0000000); //object number 388
	CreateDynamicObject(19460,-196.6000061,-1779.8000488,679.9000244,0.0000000,179.9945068,90.0000000); //object number 389
	CreateDynamicObject(19460,-212.1000061,-1779.8000488,679.9000244,0.0000000,179.9945068,90.0000000); //object number 390
	CreateDynamicObject(19460,-212.1000061,-1775.0999756,679.9000244,0.0000000,179.9945068,90.0000000); //object number 391
	CreateDynamicObject(19460,-212.1000061,-1774.9000244,679.9000244,0.0000000,179.9945068,90.0000000); //object number 392
	CreateDynamicObject(19460,-212.1000061,-1770.3000488,679.9000244,0.0000000,179.9945068,90.0000000); //object number 393
	CreateDynamicObject(19460,-212.1000061,-1770.0999756,679.9000244,0.0000000,179.9945068,90.0000000); //object number 394
	CreateDynamicObject(19460,-212.1000061,-1765.5000000,679.9000244,0.0000000,179.9945068,90.0000000); //object number 395
	CreateDynamicObject(19460,-195.5000000,-1778.0999756,679.9000244,0.0000000,179.9945068,0.0000000); //object number 396
	CreateDynamicObject(19460,-195.5000000,-1787.6999512,679.9000244,0.0000000,179.9945068,0.0000000); //object number 397
	CreateDynamicObject(19460,-200.3999939,-1792.0999756,679.9000244,0.0000000,179.9945068,90.0000000); //object number 398
	CreateDynamicObject(19460,-210.0000000,-1792.0999756,679.9000244,0.0000000,179.9945068,90.0000000); //object number 399
	CreateDynamicObject(19460,-214.5000000,-1787.6999512,679.9000244,0.0000000,179.9945068,0.0000000); //object number 400
	CreateDynamicObject(19460,-214.5000000,-1768.5000000,679.9000244,0.0000000,179.9945068,0.0000000); //object number 401
	CreateDynamicObject(19460,-214.5000000,-1778.0999756,679.9000244,0.0000000,179.9945068,0.0000000); //object number 402
	CreateDynamicObject(19460,-200.3000031,-1785.0999756,679.9000244,0.0000000,179.9945068,90.0000000); //object number 403
	CreateDynamicObject(19460,-200.3000031,-1785.3000488,679.9000244,0.0000000,179.9945068,90.0000000); //object number 404
	CreateDynamicObject(19460,-209.8999939,-1785.3000488,679.9000244,0.0000000,179.9945068,90.0000000); //object number 405
	CreateDynamicObject(19460,-209.8999939,-1785.0999756,679.9000244,0.0000000,179.9945068,90.0000000); //object number 406
	CreateDynamicObject(19460,-209.8999939,-1790.1999512,679.9000244,0.0000000,179.9945068,0.0000000); //object number 407
	CreateDynamicObject(19460,-209.6999969,-1790.1999512,679.9000244,0.0000000,179.9945068,0.0000000); //object number 408
	CreateDynamicObject(19460,-204.3000031,-1790.1999512,679.9000244,0.0000000,179.9945068,0.0000000); //object number 409
	CreateDynamicObject(19460,-200.3000031,-1790.1999512,679.9000244,0.0000000,179.9945068,0.0000000); //object number 410
	CreateDynamicObject(19460,-200.1000061,-1790.1999512,679.9000244,0.0000000,179.9945068,0.0000000); //object number 411
	CreateDynamicObject(19460,-209.6999969,-1792.1979980,673.2999878,0.0000000,0.0000000,90.0000000); //object number 412
	CreateDynamicObject(19460,-200.1000061,-1792.1979980,673.2999878,0.0000000,0.0000000,90.0000000); //object number 413
	CreateDynamicObject(2885,-200.8999939,-1775.0000000,678.4000244,270.0000000,180.0000000,180.0000000); //object number 414
	CreateDynamicObject(2885,-200.8999939,-1781.6999512,678.4000244,270.0000000,180.0000000,180.0000000); //object number 415
	CreateDynamicObject(2885,-200.8999939,-1788.4000244,678.4000244,270.0000000,0.0000000,0.0000000); //object number 416
	CreateDynamicObject(2885,-211.8000031,-1788.4000244,678.4000244,270.0000000,0.0000000,0.0000000); //object number 417
	CreateDynamicObject(2885,-211.8000031,-1781.6999512,678.4000244,270.0000000,0.0000000,0.0000000); //object number 418
	CreateDynamicObject(2885,-211.8000031,-1775.0000000,678.4000244,270.0000000,0.0000000,0.0000000); //object number 419
	CreateDynamicObject(2885,-211.8000031,-1768.3000488,678.4000244,270.0000000,0.0000000,0.0000000); //object number 420
	CreateDynamicObject(19460,-201.5010071,-1780.5000000,679.9010010,0.0000000,179.9945068,0.0000000); //object number 421
	CreateDynamicObject(19460,-207.3009949,-1780.4000244,679.9010010,0.0000000,179.9945068,0.0000000); //object number 422
	CreateDynamicObject(19430,-209.0000000,-1785.2010498,676.5000000,0.0000000,0.0000000,270.0000000); //object number 423
	CreateDynamicObject(19430,-204.6000061,-1785.1999512,676.5000000,0.0000000,0.0000000,270.0000000); //object number 424
	CreateDynamicObject(19430,-204.0000000,-1785.2010498,676.5000000,0.0000000,0.0000000,270.0000000); //object number 425
	CreateDynamicObject(14487,-211.8000031,-1768.0000000,678.0999756,0.0000000,0.0000000,0.0000000); //object number 426
	CreateDynamicObject(14487,-211.8000031,-1773.5000000,678.0999756,0.0000000,0.0000000,0.0000000); //object number 427
	CreateDynamicObject(19460,-218.5480042,-1785.1979980,673.2999878,0.0000000,0.0000000,90.0000000); //object number 431
	CreateDynamicObject(19368,-210.6260071,-1785.1979980,673.2999878,0.0000000,0.0000000,90.0000000); //object number 432
	CreateDynamicObject(19368,-209.3370056,-1785.1970215,673.2999878,0.0000000,0.0000000,90.0000000); //object number 433
	CreateDynamicObject(19368,-204.6260071,-1785.1979980,673.2999878,0.0000000,0.0000000,90.0000000); //object number 434
	CreateDynamicObject(19368,-204.1369934,-1785.1970215,673.2999878,0.0000000,0.0000000,90.0000000); //object number 435
	CreateDynamicObject(19368,-199.4259949,-1785.1979980,673.2999878,0.0000000,0.0000000,90.0000000); //object number 436
	CreateDynamicObject(19368,-199.3370056,-1785.1970215,673.2999878,0.0000000,0.0000000,90.0000000); //object number 437
	CreateDynamicObject(19368,-194.6260071,-1785.1979980,673.2999878,0.0000000,0.0000000,90.0000000); //object number 438
	CreateDynamicObject(19460,-205.6999969,-1790.1999512,679.9000244,0.0000000,179.9945068,0.0000000); //object number 439
	CreateDynamicObject(19449,-205.6000061,-1790.0000000,676.5000000,0.0000000,0.0000000,0.0000000); //object number 440
	CreateDynamicObject(19379,-210.8000031,-1790.0000000,674.7000122,0.0000000,90.0000000,0.0000000); //object number 441
	CreateDynamicObject(19379,-200.3000031,-1790.0000000,674.7000122,0.0000000,90.0000000,0.0000000); //object number 442
	CreateDynamicObject(19460,-218.5480042,-1785.2010498,673.2999878,0.0000000,0.0000000,90.0000000); //object number 443
	CreateDynamicObject(19368,-210.6250000,-1785.2010498,673.2999878,0.0000000,0.0000000,90.0000000); //object number 444
	CreateDynamicObject(19368,-209.3370056,-1785.2015381,673.2999878,0.0000000,0.0000000,90.0000000); //object number 445
	CreateDynamicObject(19368,-204.6250000,-1785.2010498,673.2999878,0.0000000,0.0000000,90.0000000); //object number 446
	CreateDynamicObject(19368,-204.1369934,-1785.2015381,673.2999878,0.0000000,0.0000000,90.0000000); //object number 447
	CreateDynamicObject(19368,-199.4250031,-1785.2010498,673.2999878,0.0000000,0.0000000,90.0000000); //object number 448
	CreateDynamicObject(19368,-199.3370056,-1785.2004395,673.2999878,0.0000000,0.0000000,90.0000000); //object number 449
	CreateDynamicObject(19368,-194.6250000,-1785.2010498,673.2999878,0.0000000,0.0000000,90.0000000); //object number 450
	CreateDynamicObject(19379,-212.6000061,-1768.5000000,674.7000122,0.0000000,90.0000000,0.0000000); //object number 451
	CreateDynamicObject(19379,-212.6000061,-1774.9000244,674.7009888,0.0000000,90.0000000,0.0000000); //object number 452
	CreateDynamicObject(19460,-209.8009949,-1789.9899902,673.2999878,0.0000000,0.0000000,0.0000000); //object number 453
	CreateDynamicObject(19460,-209.7980042,-1790.0000000,673.2999878,0.0000000,0.0000000,0.0000000); //object number 454
	CreateDynamicObject(19460,-205.6009979,-1790.0000000,673.2999878,0.0000000,0.0000000,0.0000000); //object number 455
	CreateDynamicObject(19460,-204.3979950,-1790.0000000,673.2999878,0.0000000,0.0000000,0.0000000); //object number 456
	CreateDynamicObject(19460,-200.2010040,-1789.9998779,673.2999878,0.0000000,0.0000000,0.0000000); //object number 457
	CreateDynamicObject(19460,-200.1979980,-1790.0000000,673.2999878,0.0000000,0.0000000,0.0000000); //object number 458
	CreateDynamicObject(1844,-196.0000000,-1771.5999756,674.7999878,0.0000000,0.0000000,270.0000000); //object number 459
	CreateDynamicObject(1848,-196.0000000,-1767.5999756,674.7999878,0.0000000,0.0000000,270.0000000); //object number 460
	CreateDynamicObject(1884,-198.8000031,-1772.5999756,674.7999878,0.0000000,0.0000000,270.0000000); //object number 461
	CreateDynamicObject(1885,-200.8000031,-1773.8000488,674.7999878,0.0000000,0.0000000,0.0000000); //object number 462
	CreateDynamicObject(1889,-198.8000031,-1766.5999756,674.7999878,0.0000000,0.0000000,270.0000000); //object number 463
	CreateDynamicObject(1890,-198.8000031,-1769.5999756,674.7999878,0.0000000,0.0000000,270.0000000); //object number 464
	CreateDynamicObject(1983,-198.8000031,-1764.5999756,674.7999878,0.0000000,0.0000000,180.0000000); //object number 465
	CreateDynamicObject(1984,-197.1000061,-1761.9000244,674.7999878,0.0000000,0.0000000,180.0000000); //object number 466
	CreateDynamicObject(1885,-196.0000000,-1764.4000244,674.7999878,0.0000000,0.0000000,0.0000000); //object number 467
	CreateDynamicObject(1991,-196.0000000,-1773.5000000,674.7999878,0.0000000,0.0000000,270.0000000); //object number 468
	CreateDynamicObject(1996,-196.0000000,-1774.5000000,674.7999878,0.0000000,0.0000000,270.0000000); //object number 469
	CreateDynamicObject(2362,-196.6000061,-1761.9000244,675.7299805,0.0000000,0.0000000,320.0000000); //object number 470
	CreateDynamicObject(1883,-198.3000031,-1777.1999512,674.7999878,0.0000000,0.0000000,0.0000000); //object number 471
	CreateDynamicObject(1846,-198.3000031,-1777.1999512,676.7000122,0.0000000,180.0000000,180.0000000); //object number 472
	CreateDynamicObject(1990,-196.0000000,-1759.4000244,674.7999878,0.0000000,0.0000000,0.0000000); //object number 473
	CreateDynamicObject(1990,-196.8999939,-1759.4000244,674.7999878,0.0000000,0.0000000,0.0000000); //object number 474
	CreateDynamicObject(1775,-198.6000061,-1759.4000244,675.9000244,0.0000000,0.0000000,0.0000000); //object number 475
	CreateDynamicObject(1776,-201.8999939,-1752.3000488,675.9000244,0.0000000,0.0000000,270.0000000); //object number 476
	CreateDynamicObject(1886,-200.8999939,-1759.5000000,678.2999878,19.9759827,2.9261780,22.9995728); //object number 477
	CreateDynamicObject(1886,-195.8000031,-1769.4000244,678.2999878,19.9731445,2.9223633,332.9943848); //object number 478
	CreateDynamicObject(1886,-201.0000000,-1779.0000000,678.2999878,19.9676514,2.9223633,164.9901123); //object number 479
	CreateDynamicObject(19460,-201.3999939,-1769.0999756,673.2999878,0.0000000,0.0000000,0.0000000); //object number 485
	CreateDynamicObject(1649,-201.3999939,-1778.0000000,676.4000244,0.0000000,90.0000000,270.0000000); //object number 487
	CreateDynamicObject(1649,-201.3994141,-1778.0000000,676.4000244,0.0000000,90.0000000,89.7484436); //object number 488
	CreateDynamicObject(1649,-201.3999939,-1771.6999512,676.5999756,0.0000000,0.0000000,90.0000000); //object number 489
	CreateDynamicObject(1649,-201.3999939,-1767.3000488,676.5999756,0.0000000,0.0000000,90.0000000); //object number 490
	CreateDynamicObject(19430,-201.3999939,-1764.5000000,676.5000000,0.0000000,0.0000000,179.9945068); //object number 491
	CreateDynamicObject(1649,-201.3994141,-1767.2998047,676.5999756,0.0000000,0.0000000,270.0000000); //object number 492
	CreateDynamicObject(1649,-201.3994141,-1771.6992188,676.5999756,0.0000000,0.0000000,270.0000000); //object number 493
	CreateDynamicObject(1649,-199.1999969,-1779.6999512,676.5999756,0.0000000,0.0000000,0.0000000); //object number 494
	CreateDynamicObject(19430,-196.1000061,-1779.6999512,676.5000000,0.0000000,0.0000000,90.0000000); //object number 495
	CreateDynamicObject(19460,-192.2010040,-1779.7010498,673.2999878,0.0000000,0.0000000,90.0000000); //object number 496
	CreateDynamicObject(1649,-199.1992188,-1779.6992188,676.5999756,0.0000000,0.0000000,180.0000000); //object number 497
	CreateDynamicObject(2811,-201.0000000,-1779.3000488,674.7999878,0.0000000,0.0000000,139.9908447); //object number 498
	CreateDynamicObject(3657,-206.8000031,-1765.5999756,675.2999878,0.0000000,0.0000000,90.0000000); //object number 499
	CreateDynamicObject(2636,-196.1000061,-1780.3000488,675.4000244,0.0000000,0.0000000,0.0000000); //object number 500
	CreateDynamicObject(2637,-197.1000061,-1780.9000244,675.2000122,0.0000000,0.0000000,270.0000000); //object number 501
	CreateDynamicObject(2637,-200.1999969,-1780.9000244,675.2000122,0.0000000,0.0000000,270.0000000); //object number 502
	CreateDynamicObject(2637,-208.5000000,-1780.9000244,675.2000122,0.0000000,0.0000000,270.0000000); //object number 503
	CreateDynamicObject(2637,-212.3000031,-1780.9000244,675.2000122,0.0000000,0.0000000,270.0000000); //object number 504
	CreateDynamicObject(2636,-196.1000061,-1781.4000244,675.4000244,0.0000000,0.0000000,0.0000000); //object number 505
	CreateDynamicObject(2636,-199.3000031,-1781.4000244,675.4000244,0.0000000,0.0000000,0.0000000); //object number 506
	CreateDynamicObject(2636,-199.3000031,-1780.4000244,675.4000244,0.0000000,0.0000000,0.0000000); //object number 507
	CreateDynamicObject(2636,-207.6000061,-1780.4000244,675.4000244,0.0000000,0.0000000,0.0000000); //object number 508
	CreateDynamicObject(2636,-207.6000061,-1781.4000244,675.4000244,0.0000000,0.0000000,0.0000000); //object number 509
	CreateDynamicObject(2636,-211.3999939,-1781.4000244,675.4000244,0.0000000,0.0000000,0.0000000); //object number 510
	CreateDynamicObject(2636,-211.3999939,-1780.4000244,675.4000244,0.0000000,0.0000000,0.0000000); //object number 511
	CreateDynamicObject(2636,-213.3000031,-1780.4000244,675.4000244,0.0000000,0.0000000,180.0000000); //object number 512
	CreateDynamicObject(2636,-213.3000031,-1781.4000244,675.4000244,0.0000000,0.0000000,179.9945068); //object number 513
	CreateDynamicObject(2636,-209.5000000,-1781.4000244,675.4000244,0.0000000,0.0000000,179.9945068); //object number 514
	CreateDynamicObject(2636,-209.5000000,-1780.3000488,675.4000244,0.0000000,0.0000000,179.9945068); //object number 515
	CreateDynamicObject(2636,-201.1999969,-1780.3000488,675.4000244,0.0000000,0.0000000,179.9945068); //object number 516
	CreateDynamicObject(2636,-201.1999969,-1781.3000488,675.4000244,0.0000000,0.0000000,179.9945068); //object number 517
	CreateDynamicObject(2636,-198.0000000,-1781.3000488,675.4000244,0.0000000,0.0000000,179.9945068); //object number 518
	CreateDynamicObject(2636,-198.0000000,-1780.3000488,675.4000244,0.0000000,0.0000000,179.9945068); //object number 519
	CreateDynamicObject(1796,-210.1999969,-1778.5999756,674.7999878,0.0000000,0.0000000,0.0000000); //object number 520
	CreateDynamicObject(1796,-213.3999939,-1787.8000488,674.7999878,0.0000000,0.0000000,270.0000000); //object number 521
	CreateDynamicObject(1796,-213.3999939,-1790.5000000,674.7999878,0.0000000,0.0000000,270.0000000); //object number 522
	CreateDynamicObject(1796,-209.1999969,-1790.5000000,674.7999878,0.0000000,0.0000000,270.0000000); //object number 523
	CreateDynamicObject(1796,-209.1999969,-1787.8000488,674.7999878,0.0000000,0.0000000,270.0000000); //object number 524
	CreateDynamicObject(1796,-203.8000031,-1787.8000488,674.7999878,0.0000000,0.0000000,270.0000000); //object number 525
	CreateDynamicObject(1796,-199.0000000,-1787.8000488,674.7999878,0.0000000,0.0000000,270.0000000); //object number 526
	CreateDynamicObject(1796,-203.8000031,-1790.5000000,674.7999878,0.0000000,0.0000000,270.0000000); //object number 527
	CreateDynamicObject(1796,-199.0000000,-1790.5000000,674.7999878,0.0000000,0.0000000,270.0000000); //object number 528
	CreateDynamicObject(1796,-212.8999939,-1778.5999756,674.7999878,0.0000000,0.0000000,0.0000000); //object number 529
	CreateDynamicObject(1796,-212.8999939,-1773.8000488,674.7999878,0.0000000,0.0000000,0.0000000); //object number 530
	CreateDynamicObject(1796,-212.8999939,-1769.0000000,674.7999878,0.0000000,0.0000000,0.0000000); //object number 531
	CreateDynamicObject(1796,-210.1999969,-1773.8000488,674.7999878,0.0000000,0.0000000,0.0000000); //object number 532
	CreateDynamicObject(1796,-210.1999969,-1769.0000000,674.7999878,0.0000000,0.0000000,0.0000000); //object number 533
	CreateDynamicObject(2811,-206.8999939,-1774.9000244,674.7999878,0.0000000,0.0000000,95.9908447); //object number 534
	CreateDynamicObject(1523,-207.3500061,-1769.2509766,674.7399902,0.0000000,0.0000000,90.0000000); //object number 535
	CreateDynamicObject(1523,-207.3500061,-1774.0520020,674.7399902,0.0000000,0.0000000,90.0000000); //object number 536
	CreateDynamicObject(1523,-207.3500061,-1777.2509766,674.7399902,0.0000000,0.0000000,90.0000000); //object number 537
	CreateDynamicObject(1523,-212.2100067,-1785.1700439,674.7399902,0.0000000,0.0000000,180.0000000); //object number 538
	CreateDynamicObject(1523,-206.2100067,-1785.1700439,674.7399902,0.0000000,0.0000000,179.9945068); //object number 539
	CreateDynamicObject(1523,-201.0079956,-1785.1700439,674.7399902,0.0000000,0.0000000,179.9945068); //object number 540
	CreateDynamicObject(1523,-196.2100067,-1785.1700439,674.7399902,0.0000000,0.0000000,179.9945068); //object number 541
	CreateDynamicObject(3808,-207.2500000,-1767.5000000,676.2999878,0.0000000,0.0000000,0.0000000); //object number 542
	CreateDynamicObject(3808,-207.2500000,-1772.2900391,676.2999878,0.0000000,0.0000000,0.0000000); //object number 543
	CreateDynamicObject(3808,-207.2500000,-1775.5000000,676.2999878,0.0000000,0.0000000,0.0000000); //object number 544
	CreateDynamicObject(3808,-214.0000000,-1785.0500488,676.5000000,0.0000000,0.0000000,90.0000000); //object number 545
	CreateDynamicObject(3808,-208.0000000,-1785.0500488,676.5000000,0.0000000,0.0000000,90.0000000); //object number 546
	CreateDynamicObject(3808,-202.8000031,-1785.0500488,676.5000000,0.0000000,0.0000000,90.0000000); //object number 547
	CreateDynamicObject(3808,-198.0000000,-1785.0500488,676.5000000,0.0000000,0.0000000,90.0000000); //object number 548
	CreateDynamicObject(16101,-207.3300018,-1767.6999512,666.2999878,0.0000000,0.0000000,0.0000000); //object number 549
	CreateDynamicObject(16101,-207.3329926,-1769.2800293,666.2999878,0.0000000,0.0000000,0.0000000); //object number 550
	CreateDynamicObject(16101,-207.3300018,-1772.5000000,666.2999878,0.0000000,0.0000000,0.0000000); //object number 551
	CreateDynamicObject(16101,-207.3300018,-1774.0000000,666.2999878,0.0000000,0.0000000,0.0000000); //object number 552
	CreateDynamicObject(16101,-207.3300018,-1775.6999512,666.2999878,0.0000000,0.0000000,0.0000000); //object number 553
	CreateDynamicObject(16101,-207.3300018,-1777.2800293,666.2999878,0.0000000,0.0000000,0.0000000); //object number 554
	CreateDynamicObject(16101,-213.7799988,-1785.1300049,666.2999878,0.0000000,0.0000000,0.0000000); //object number 555
	CreateDynamicObject(16101,-212.2100067,-1785.1300049,666.2999878,0.0000000,0.0000000,0.0000000); //object number 556
	CreateDynamicObject(16101,-207.7799988,-1785.1300049,666.2999878,0.0000000,0.0000000,0.0000000); //object number 557
	CreateDynamicObject(16101,-206.2100067,-1785.1300049,666.2999878,0.0000000,0.0000000,0.0000000); //object number 558
	CreateDynamicObject(16101,-202.5800018,-1785.1300049,666.2999878,0.0000000,0.0000000,0.0000000); //object number 559
	CreateDynamicObject(16101,-201.0099945,-1785.1300049,666.2999878,0.0000000,0.0000000,0.0000000); //object number 560
	CreateDynamicObject(16101,-197.7799988,-1785.1300049,666.2999878,0.0000000,0.0000000,0.0000000); //object number 561
	CreateDynamicObject(16101,-196.2100067,-1785.1300049,666.2999878,0.0000000,0.0000000,0.0000000); //object number 562
	CreateDynamicObject(3657,-201.8999939,-1758.9000244,675.2999878,0.0000000,0.0000000,270.0000000); //object number 563
	CreateDynamicObject(1776,-199.8994141,-1759.3994141,675.9000244,0.0000000,0.0000000,0.0000000); //object number 564
	CreateDynamicObject(19329,-201.4100000,-1767.3000000,676.0400000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(19326,-201.4100000,-1771.6800000,676.0400000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(19329,-201.4100000,-1778.0300000,676.0400000,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(19326,-199.1800000,-1779.7000000,676.0400000,0.0000000,0.0000000,180.0000000); //
	CreateDynamicObject(19327,-210.5600000,-1779.9000000,676.7500000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19328,-195.5900000,-1777.1900000,676.7700000,0.0000000,0.0000000,270.0000000); //
	CreateDynamicObject(11435,-204.3999939,-1745.0999756,679.4000244,0.0000000,0.0000000,270.0000000); //object number 285
	CreateDynamicObject(11435,-204.3994141,-1758.7998047,679.4000244,0.0000000,0.0000000,270.0000000); //object number 287
	CreateDynamicObject(11435,-198.6000061,-1755.0000000,679.4000244,0.0000000,0.0000000,270.0000000); //object number 303
	CreateDynamicObject(11435,-198.6000061,-1750.9000244,679.4000244,0.0000000,0.0000000,270.0000000); //object number 304
	CreateDynamicObject(11435,-204.3999939,-1772.5000000,679.4000244,0.0000000,0.0000000,270.0000000); //object number 429
	CreateDynamicObject(11435,-201.3999939,-1774.4000244,679.4000244,0.0000000,0.0000000,270.0000000); //object number 480
	CreateDynamicObject(11435,-201.3999939,-1765.6999512,679.4000244,0.0000000,0.0000000,270.0000000); //object number 481
	CreateDynamicObject(11435,-201.3999939,-1770.0000000,679.4000244,0.0000000,0.0000000,270.0000000); //object number 482
	CreateDynamicObject(11435,-201.3999939,-1776.8000488,679.4000244,0.0000000,0.0000000,270.0000000); //object number 483
	CreateDynamicObject(11435,-201.3999939,-1780.1999512,679.4000244,0.0000000,0.0000000,270.0000000); //object number 484
	CreateDynamicObject(11435,-197.0000000,-1780.1999512,679.4000244,0.0000000,0.0000000,270.0000000); //object number 486

	/*
	Objects converted: 741
	Vehicles converted: 0
	Vehicle models found: 0
	----------------------
	In the time this conversion took to finish the US national debt has risen by about $3,732.49!
	*/

    // Doors & Cells
	door0 = CreateDynamicObject(1495,1487.0000000,-1762.4250488,3284.2360840,0.0000000,0.0000000,270.0000000); //object(gen_doorext01)(1)
	door1 = CreateDynamicObject(1495,1483.7900391,-1762.4250488,3284.2360840,0.0000000,0.0000000,270.0000000); //object(gen_doorext01)(2)
	door2 = CreateDynamicObject(1495,1479.8599853,-1758.3199463,3284.2338867,0.0000000,0.0000000,0.0000000); //object(gen_doorext01)(2)
	door3 = CreateDynamicObject(1495,1467.0670166,-1758.3199463,3284.2338867,0.0000000,0.0000000,0.0000000); //object(gen_doorext01)(2)
	cell0 = CreateDynamicObject(1567,1491.2148438,-1764.9000244,3284.2504883,0.0000000,0.0000000,0.0000000); //object(gen_wardrobe)(2)
	cell1 = CreateDynamicObject(1567,1494.4121094,-1764.9000244,3284.2504883,0.0000000,0.0000000,0.0000000); //object(gen_wardrobe)(3)
	cell2 = CreateDynamicObject(1567,1497.6113281,-1764.9000244,3284.2504883,0.0000000,0.0000000,0.0000000); //object(gen_wardrobe)(4)
	cell3 = CreateDynamicObject(1567,1500.8144531,-1764.9000244,3284.2504883,0.0000000,0.0000000,0.0000000); //object(gen_wardrobe)(6)
	cell4 = CreateDynamicObject(1567,1500.8199463,-1761.5100098,3284.2504883,0.0000000,0.0000000,0.0000000); //object(gen_wardrobe)(7)
	cell5 = CreateDynamicObject(1567,1491.2209473,-1761.5000000,3284.2504883,0.0000000,0.0000000,0.0000000); //object(gen_wardrobe)(8)
	cell6 = CreateDynamicObject(1567,1494.4189453,-1761.5100098,3284.2504883,0.0000000,0.0000000,0.0000000); //object(gen_wardrobe)(9)
	cell7 = CreateDynamicObject(1567,1497.6199951,-1761.5100098,3284.2504883,0.0000000,0.0000000,0.0000000); //object(gen_wardrobe)(10)
	
	// Fresh LS Objects
	CreateDynamicObject(620,1545.6804200,-1656.9262700,13.0468800,356.8584000,0.0000000,3.1415900); //
	CreateDynamicObject(620,1545.4594700,-1665.2086200,13.0468800,356.8584000,0.0000000,3.1415900); //
	CreateDynamicObject(620,1545.4919400,-1685.4586200,13.0468800,356.8584000,0.0000000,3.1415900); //
	CreateDynamicObject(620,1545.3601100,-1693.8501000,13.0468800,356.8584000,0.0000000,3.1415900); //
	CreateDynamicObject(620,1541.9401900,-1648.4858400,13.0468800,356.8584000,0.0000000,3.1415900); //
	CreateDynamicObject(620,1541.4796100,-1702.5841100,13.0468800,356.8584000,0.0000000,3.1415900); //
	CreateDynamicObject(620,1542.0035400,-1713.1943400,13.0468800,356.8584000,0.0000000,3.1415900); //
	CreateDynamicObject(620,1541.9339600,-1639.1523400,13.0468800,356.8584000,0.0000000,3.1415900); //
	CreateDynamicObject(19425,1532.2966300,-1684.4118700,12.3630600,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19425,1532.3769500,-1695.4764400,12.3630600,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19425,1532.3557100,-1704.6181600,12.3630600,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19425,1526.9757100,-1704.6295200,12.3630600,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19425,1527.1573500,-1695.4484900,12.3630600,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19425,1527.2158200,-1684.4038100,12.3630600,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19425,1527.0908200,-1660.8509500,12.3630600,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19425,1532.2408400,-1660.8308100,12.3630600,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19425,1532.2271700,-1652.0647000,12.3630600,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19425,1526.9231000,-1652.0866700,12.3630600,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19425,1526.9097900,-1643.9582500,12.3630600,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19425,1532.2497600,-1643.9231000,12.3630600,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(970,1534.6626000,-1683.6281700,13.1240600,0.0000000,0.0000000,89.8800000); //
	CreateDynamicObject(970,1534.6634500,-1687.8054200,13.1240600,0.0000000,0.0000000,89.8800000); //
	CreateDynamicObject(970,1534.6527100,-1691.9510500,13.1240600,0.0000000,0.0000000,89.8800000); //
	CreateDynamicObject(970,1534.6446500,-1696.1082800,13.1240600,0.0000000,0.0000000,89.8800000); //
	CreateDynamicObject(970,1534.7087400,-1661.7655000,13.0554800,0.0000000,0.0000000,-90.3000200); //
	CreateDynamicObject(970,1534.7432900,-1657.5876500,13.0554800,0.0000000,0.0000000,-90.3000200); //
	CreateDynamicObject(970,1534.7462200,-1653.4418900,13.0554800,0.0000000,0.0000000,-90.1200200); //
	CreateDynamicObject(970,1534.7706300,-1649.2484100,13.0554800,0.0000000,0.0000000,-90.1200200); //
	CreateDynamicObject(1232,1535.3662100,-1682.3599900,15.1148000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1232,1535.1048600,-1663.3403300,15.1148000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(7090,1554.9498300,-1675.6342800,25.0206100,0.0000000,0.0000000,-180.5399900); //
	CreateDynamicObject(1257,1522.4171100,-1677.8636500,13.7798600,0.0000000,0.0000000,179.5200700); //
	CreateDynamicObject(620,1533.2656300,-1749.0234400,12.8046900,356.8584000,0.0000000,3.1415900); //
	CreateDynamicObject(1291,2055.6921400,-1897.5388200,13.0057900,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1231,2045.7457300,-1897.8068800,15.2582400,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1366,2044.7370600,-1926.6272000,13.0592000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1280,2047.7855200,-1897.5493200,12.9503800,0.0000000,0.0000000,90.7200000); //
	CreateDynamicObject(1280,2050.9550800,-1897.5516400,12.9503800,0.0000000,0.0000000,90.7200000); //
	CreateDynamicObject(970,2061.2714800,-1922.3447300,13.0628100,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(970,2069.5813000,-1922.3437500,13.0628100,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(970,2065.4409200,-1922.3480200,13.0628100,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(970,2071.6826200,-1920.2850300,13.0628100,0.0000000,0.0000000,-90.1200200); //
	CreateDynamicObject(970,2071.6911600,-1903.1680900,13.0628100,0.0000000,0.0000000,-90.1200200); //
	CreateDynamicObject(970,2071.6767600,-1907.3316700,13.0628100,0.0000000,0.0000000,-90.1200200); //
	CreateDynamicObject(970,2051.9838900,-1922.3533900,13.0628100,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(970,2049.9130900,-1920.2670900,13.0628100,0.0000000,0.0000000,-90.1200200); //
	CreateDynamicObject(970,2049.9003900,-1916.1308600,13.0628100,0.0000000,0.0000000,-90.1200200); //
	CreateDynamicObject(970,2049.8862300,-1903.1773700,13.0628100,0.0000000,0.0000000,-90.1200200); //
	CreateDynamicObject(970,2069.6059600,-1901.0699500,13.0628100,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(970,2065.4450700,-1901.1115700,13.0628100,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(970,2056.0859400,-1901.0915500,13.0628100,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(970,2051.9265100,-1901.0827600,13.0628100,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(970,2049.8913600,-1907.3795200,13.0628100,0.0000000,0.0000000,-90.1200200); //
	CreateDynamicObject(1231,2045.6894500,-1922.0709200,15.2582400,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1231,2072.2592800,-1921.9887700,15.2582400,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1231,2072.2849100,-1901.3552200,15.2582400,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(620,2097.6396500,-1783.0146500,10.8046900,356.8584000,0.0000000,3.1415900); //
	CreateDynamicObject(620,2099.1093800,-1776.4847400,10.8046900,356.8584000,0.0000000,3.1415900); //
	CreateDynamicObject(620,2100.2253400,-1770.4223600,10.8046900,356.8584000,0.0000000,3.1415900); //
	CreateDynamicObject(620,2110.7773400,-1830.0234400,10.8046900,356.8584000,0.0000000,3.1415900); //
	CreateDynamicObject(620,2132.8186000,-1794.2241200,10.8046900,356.8584000,0.0000000,3.1415900); //
	CreateDynamicObject(620,2133.4130900,-1829.0520000,10.8046900,356.8584000,0.0000000,3.1415900); //
	CreateDynamicObject(620,2132.9326200,-1811.8182400,10.8046900,356.8584000,0.0000000,3.1415900); //
	CreateDynamicObject(1257,2095.6577100,-1767.7927200,13.6453400,0.0000000,0.0000000,-14.8200000); //
	CreateDynamicObject(1231,2100.3369100,-1801.4951200,15.3132600,0.0000000,0.0000000,90.9600000); //
	CreateDynamicObject(1231,2100.3999000,-1812.0427200,15.3132600,0.0000000,0.0000000,90.9600000); //
	CreateDynamicObject(910,2124.3107900,-1792.6251200,13.7806600,0.0000000,0.0000000,88.9799800); //
	CreateDynamicObject(970,1724.7053200,-1288.7753900,13.0599700,0.0000000,0.0000000,89.8800100); //
	CreateDynamicObject(970,1724.7066700,-1284.6093800,13.0599700,0.0000000,0.0000000,89.8800100); //
	CreateDynamicObject(970,1724.7093500,-1280.4299300,13.0599700,0.0000000,0.0000000,89.8800100); //
	CreateDynamicObject(970,1724.7028800,-1270.7002000,13.0599700,0.0000000,0.0000000,89.8800100); //
	CreateDynamicObject(970,1724.7026400,-1266.5383300,13.0599700,0.0000000,0.0000000,89.8800100); //
	CreateDynamicObject(970,1724.6942100,-1262.3739000,13.0599700,0.0000000,0.0000000,89.8800100); //
	CreateDynamicObject(970,1724.6976300,-1258.2171600,13.0599700,0.0000000,0.0000000,89.8800100); //
	CreateDynamicObject(970,1730.4379900,-1290.8533900,13.0599700,0.0000000,0.0000000,182.2201100); //
	CreateDynamicObject(970,1734.6068100,-1290.6366000,13.0599700,0.0000000,0.0000000,183.3002200); //
	CreateDynamicObject(970,1738.7385300,-1290.1022900,13.0599700,0.0000000,0.0000000,192.3002300); //
	CreateDynamicObject(970,1742.8315400,-1289.2591600,13.0599700,0.0000000,0.0000000,190.9802900); //
	CreateDynamicObject(1280,1737.0368700,-1278.3483900,12.8847500,0.0000000,0.0000000,-37.5600000); //
	CreateDynamicObject(1280,1732.8048100,-1283.7211900,12.8847500,0.0000000,0.0000000,-37.5600000); //
	CreateDynamicObject(1280,1734.8502200,-1281.0603000,12.8847500,0.0000000,0.0000000,-37.5600000); //
	CreateDynamicObject(1211,1720.4331100,-1280.3973400,12.9981400,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1216,1731.9217500,-1285.7288800,13.2170300,0.0000000,0.0000000,-74.8800000); //
	CreateDynamicObject(1216,1732.2795400,-1287.1334200,13.2170300,0.0000000,0.0000000,-74.8800000); //
	CreateDynamicObject(1216,1732.6046100,-1288.5015900,13.2170300,0.0000000,0.0000000,-76.6200000); //
	CreateDynamicObject(1232,1735.6949500,-1289.4013700,15.2108700,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1232,1743.7348600,-1288.2127700,15.2108700,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1232,1732.0874000,-1263.6234100,15.2108700,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1232,1741.2343800,-1271.4563000,15.2108700,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(853,2232.4709500,-1688.6076700,13.3769500,0.0000000,0.0000000,-30.6000000); //
	CreateDynamicObject(851,2246.4675300,-1690.9896200,13.0505100,0.0000000,0.0000000,-24.8400000); //
	CreateDynamicObject(1431,2241.3469200,-1687.7467000,13.3521000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1359,2105.3603500,-1809.0468800,13.2089900,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1358,2278.8127400,-1694.5191700,13.8599200,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1338,2235.8852500,-1691.6602800,13.5638300,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(620,2216.3979500,-1675.6550300,12.0937500,356.8584000,0.0000000,3.1415900); //
	CreateDynamicObject(620,2211.5234400,-1701.9177200,12.0937500,356.8584000,0.0000000,3.1415900); //
	CreateDynamicObject(620,2201.3335000,-1659.2896700,12.0937500,356.8584000,0.0000000,3.1415900); //
	CreateDynamicObject(620,2198.4182100,-1670.7878400,12.0937500,356.8584000,0.0000000,3.1415900); //
	CreateDynamicObject(620,2195.4790000,-1684.8138400,12.0937500,356.8584000,0.0000000,3.1415900); //
	CreateDynamicObject(620,2193.7583000,-1700.5700700,12.0937500,356.8584000,0.0000000,3.1415900); //
	CreateDynamicObject(620,2192.3374000,-1715.7343800,12.0937500,356.8584000,0.0000000,3.1415900); //
	CreateDynamicObject(979,1942.2506100,-1769.2077600,13.3890300,0.0000000,0.0000000,-89.8200000); //
	CreateDynamicObject(979,1942.2783200,-1776.1661400,13.3890300,0.0000000,0.0000000,-89.8200000); //
	CreateDynamicObject(979,1940.9500700,-1776.0964400,13.3890300,0.0000000,0.0000000,-89.8200000); //
	CreateDynamicObject(979,1940.9417700,-1769.1552700,13.3890300,0.0000000,0.0000000,-90.3000000); //
	CreateDynamicObject(712,2097.2463400,-1788.5688500,21.3906300,356.8584000,0.0000000,3.1415900); //
	CreateDynamicObject(712,2093.0490700,-1824.4261500,21.3906300,356.8584000,0.0000000,3.1415900); //
	CreateDynamicObject(712,2099.8603500,-1829.1527100,21.3906300,356.8584000,0.0000000,3.1415900); //
	
	// Dealership 1
	
	CreateDynamicObject(8435,332.0908800,1299.9794900,448.4752500,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19353,344.5591400,1296.7412100,453.6435900,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19353,344.5537100,1293.5379600,453.6435900,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19353,344.5331100,1290.3773200,453.6435900,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19353,344.5293300,1287.2370600,453.6435900,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19353,344.5254500,1284.1368400,453.6435900,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19353,344.5182500,1280.9965800,453.6435900,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19353,342.8738400,1279.8029800,453.6435900,0.0000000,0.0000000,-90.0000000); //
	CreateDynamicObject(19353,339.6969600,1279.8075000,453.6435900,0.0000000,0.0000000,-90.0000000); //
	CreateDynamicObject(19353,336.6169100,1279.7817400,453.6435900,0.0000000,0.0000000,-90.0000000); //
	CreateDynamicObject(19353,333.5164500,1279.8159200,453.6435900,0.0000000,0.0000000,-90.0000000); //
	CreateDynamicObject(19353,330.3436300,1279.8071300,453.6435900,0.0000000,0.0000000,-90.0000000); //
	CreateDynamicObject(19353,328.8477800,1281.4768100,453.6435900,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19353,328.8603800,1284.5858200,453.6435900,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19353,328.8415500,1287.7310800,453.6435900,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19353,328.8581800,1290.7725800,453.6435900,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19353,328.8305400,1296.6348900,453.6435900,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19383,328.8436000,1293.6720000,453.6401400,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19353,344.5785500,1299.8615700,453.6435900,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19353,344.5817900,1303.0615200,453.6651300,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19353,344.5643900,1305.6217000,453.6435900,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19353,344.5653400,1308.7221700,453.6435900,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19353,327.3317000,1298.3234900,453.6435900,0.0000000,0.0000000,-90.0000000); //
	CreateDynamicObject(19353,324.1774600,1298.3203100,453.6435900,0.0000000,0.0000000,-90.0000000); //
	CreateDynamicObject(19353,320.9760400,1298.3000500,453.6435900,0.0000000,0.0000000,-90.0000000); //
	CreateDynamicObject(19353,317.7871700,1298.3140900,453.6435900,0.0000000,0.0000000,-90.0000000); //
	CreateDynamicObject(19353,316.3000800,1300.0000000,453.6435900,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19353,316.2985200,1303.1225600,453.6435900,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19353,316.2917500,1306.2353500,453.6435900,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19353,316.2851300,1309.4167500,453.6435900,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19353,316.2884500,1312.5766600,453.6435900,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19353,316.2951000,1315.7771000,453.6435900,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19353,316.2989500,1318.9818100,453.6435900,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19353,317.8998400,1320.5443100,453.6435900,0.0000000,0.0000000,-90.0000000); //
	CreateDynamicObject(19353,321.0794700,1320.5498000,453.6435900,0.0000000,0.0000000,-90.0000000); //
	CreateDynamicObject(19353,324.1632100,1320.5495600,453.6435900,0.0000000,0.0000000,-90.0000000); //
	CreateDynamicObject(19353,327.2847600,1320.5487100,453.6435900,0.0000000,0.0000000,-90.0000000); //
	CreateDynamicObject(19353,330.3489100,1320.5653100,453.6435900,0.0000000,0.0000000,-90.0000000); //
	CreateDynamicObject(19353,333.4104000,1320.5627400,453.6435900,0.0000000,0.0000000,-90.0000000); //
	CreateDynamicObject(19353,336.4956700,1320.5639600,453.6435900,0.0000000,0.0000000,-90.0000000); //
	CreateDynamicObject(19353,339.6652200,1320.5638400,453.6435900,0.0000000,0.0000000,-90.0000000); //
	CreateDynamicObject(19353,342.8055400,1320.5800800,453.6435900,0.0000000,0.0000000,-90.0000000); //
	CreateDynamicObject(19353,344.5335700,1318.4996300,453.6435900,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19353,344.5265800,1321.1744400,453.6435900,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(7891,344.6976000,1313.4353000,453.1127000,0.0000000,0.0000000,0.1800000); //
	CreateDynamicObject(1556,328.7863200,1292.9444600,451.8860200,0.0000000,0.0000000,90.2400100); //
	CreateDynamicObject(3281,328.9873400,1287.8029800,454.6429100,0.0000000,0.0000000,90.5400000); //
	CreateDynamicObject(3465,331.7112400,1280.4271200,453.2884200,0.0000000,0.0000000,89.2799900); //
	CreateDynamicObject(3465,335.9934700,1280.4139400,453.2884200,0.0000000,0.0000000,89.2799900); //
	CreateDynamicObject(2914,344.2162200,1289.5054900,454.0192000,0.0000000,0.0000000,89.1000200); //
	CreateDynamicObject(2914,344.3797300,1286.7127700,454.0192000,0.0000000,0.0000000,89.1000200); //
	CreateDynamicObject(1622,327.3845500,1298.8769500,455.0935700,0.0000000,0.0000000,-96.9600200); //
	CreateDynamicObject(2403,339.0202600,1285.2000700,451.9643900,0.0000000,0.0000000,-90.5999500); //
	CreateDynamicObject(2467,343.9333500,1289.5247800,451.9665500,0.0000000,0.0000000,267.7199100); //
	CreateDynamicObject(2620,331.2359300,1290.1842000,452.7216500,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(2620,328.0255400,1299.0106200,452.7216500,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(2698,333.8948100,1280.9885300,452.8956900,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1840,329.3793000,1280.0295400,454.7537500,0.0000000,0.0000000,-90.8000000); //
	CreateDynamicObject(1840,343.3932800,1282.3037100,454.7962300,0.0000000,0.0000000,-43.8800100); //
	CreateDynamicObject(1840,342.3751200,1281.0704300,454.7962300,0.0000000,0.0000000,-62.1800100); //
	CreateDynamicObject(1840,341.6473700,1280.6140100,454.7962300,0.0000000,0.0000000,-68.6600000); //
	CreateDynamicObject(1840,342.8822000,1281.7282700,454.7962300,0.0000000,0.0000000,-50.3000100); //
	CreateDynamicObject(19353,342.9647500,1296.4022200,453.6435900,0.0000000,0.0000000,-90.0000000); //
	CreateDynamicObject(19383,341.4519300,1298.0756800,453.6401400,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(2739,344.0070200,1299.2033700,451.9693000,0.0000000,0.0000000,-92.3400500); //
	CreateDynamicObject(2738,344.0344500,1297.1661400,452.5477300,0.0000000,0.0000000,-88.5600100); //
	CreateDynamicObject(19353,343.1228600,1299.5806900,453.6435900,0.0000000,0.0000000,-90.0000000); //
	CreateDynamicObject(3281,333.6421500,1320.3815900,454.6429100,0.0000000,0.0000000,0.1800000); //
	CreateDynamicObject(3281,323.1601000,1320.3621800,454.6429100,0.0000000,0.0000000,0.1800000); //
	CreateDynamicObject(2713,344.0693100,1299.3138400,452.0888400,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(2852,342.6175200,1298.1356200,451.9703400,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1491,341.4795500,1297.3302000,451.9673200,0.0000000,0.0000000,89.7000400); //
	CreateDynamicObject(1008,343.8312400,1289.1439200,452.9765600,0.0000000,0.0000000,92.9400000); //
	CreateDynamicObject(1010,343.7824400,1289.2622100,452.5804400,0.0000000,0.0000000,89.5200300); //
	CreateDynamicObject(1116,344.4490700,1291.5689700,454.1434600,0.0000000,0.0000000,88.5000000); //
	CreateDynamicObject(1115,344.3876600,1293.8831800,454.1235000,0.0000000,0.0000000,90.2399800); //
	CreateDynamicObject(1139,343.2495100,1283.7943100,452.8186600,0.0000000,0.0000000,69.4799900); //
	CreateDynamicObject(1138,341.6160600,1281.4753400,452.8452800,0.0000000,0.0000000,32.4599900); //
	CreateDynamicObject(1166,343.9069200,1283.3808600,455.0475200,0.0000000,0.0000000,66.9600100); //
	CreateDynamicObject(1840,340.8423800,1280.1989700,454.7962300,0.0000000,0.0000000,-66.6799900); //
	CreateDynamicObject(1085,316.4834300,1301.6267100,454.5632300,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1084,316.4451900,1303.3313000,454.5558500,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1083,316.5000600,1305.3985600,454.5508400,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1082,316.4715000,1307.6674800,454.5083300,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1081,316.4780900,1309.5833700,454.4835200,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1080,316.4568500,1311.5494400,454.4508700,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1079,316.4432100,1313.4891400,454.4410700,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1078,316.4613300,1315.0141600,454.4444000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1077,316.4653900,1316.5820300,454.4141800,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1076,316.4858100,1318.1606400,454.3816800,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1074,316.4744600,1300.1103500,454.6027200,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1238,331.1434900,1289.4174800,453.2226600,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(2467,343.8900500,1291.8049300,451.9665500,0.0000000,0.0000000,268.4398800); //
	CreateDynamicObject(2467,343.8224500,1294.0831300,451.9665500,0.0000000,0.0000000,268.4398800); //
	CreateDynamicObject(2412,329.1032700,1293.0611600,451.9706400,0.0000000,0.0000000,89.8200000); //
	CreateDynamicObject(2412,328.9962500,1295.0084200,451.9706400,0.0000000,0.0000000,89.8200000); //
	CreateDynamicObject(2376,336.5206600,1288.1937300,451.9204700,0.0000000,0.0000000,270.6599700); //
	CreateDynamicObject(2491,329.6375100,1298.1927500,451.9709500,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(2626,331.0559700,1288.6943400,452.3713100,0.0000000,0.0000000,88.1400000); //
	CreateDynamicObject(1215,336.7837800,1288.4957300,452.7261700,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1215,336.8479900,1285.6383100,452.7261700,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1078,336.8573900,1287.5690900,452.3273600,-0.0800000,-90.3400000,-0.4800000); //
	CreateDynamicObject(1077,336.8744500,1286.5009800,452.3073100,0.0000000,-90.0000000,0.0000000); //
	CreateDynamicObject(19448,342.8298300,1284.5354000,455.4490100,0.0000000,90.0000000,0.0000000); //
	CreateDynamicObject(19448,339.3296500,1284.5415000,455.4490100,0.0000000,90.0000000,0.0000000); //
	CreateDynamicObject(19448,335.8698400,1284.5489500,455.4490100,0.0000000,90.0000000,0.0000000); //
	CreateDynamicObject(19448,332.3696900,1284.5750700,455.4490100,0.0000000,90.0000000,0.0000000); //
	CreateDynamicObject(19448,328.8687100,1284.5820300,455.4490100,0.0000000,90.0000000,0.0000000); //
	CreateDynamicObject(19448,328.9167200,1294.2227800,455.4490100,0.0000000,90.0000000,0.0000000); //
	CreateDynamicObject(19448,332.4024700,1294.2142300,455.4490100,0.0000000,90.0000000,0.0000000); //
	CreateDynamicObject(19448,335.8826900,1294.2100800,455.4490100,0.0000000,90.0000000,0.0000000); //
	CreateDynamicObject(19448,339.3827200,1294.2061800,455.4490100,0.0000000,90.0000000,0.0000000); //
	CreateDynamicObject(19448,342.8828100,1294.2225300,455.4490100,0.0000000,90.0000000,0.0000000); //
	CreateDynamicObject(19448,342.8798500,1303.8475300,455.4490100,0.0000000,90.0000000,0.0000000); //
	CreateDynamicObject(19448,345.8433200,1313.4948700,455.4490100,0.0000000,90.0000000,0.0000000); //
	CreateDynamicObject(19448,342.9116500,1323.0401600,455.4490100,0.0000000,90.0000000,0.0000000); //
	CreateDynamicObject(19448,339.3769200,1303.8459500,455.4490100,0.0000000,90.0000000,0.0000000); //
	CreateDynamicObject(19448,335.8903200,1303.8413100,455.4490100,0.0000000,90.0000000,0.0000000); //
	CreateDynamicObject(19448,332.4101900,1303.8343500,455.4490100,0.0000000,90.0000000,0.0000000); //
	CreateDynamicObject(19448,328.9100600,1303.8540000,455.4490100,0.0000000,90.0000000,0.0000000); //
	CreateDynamicObject(19448,325.4241300,1303.0153800,455.4490100,0.0000000,90.0000000,0.0000000); //
	CreateDynamicObject(19448,321.9242200,1303.0169700,455.4490100,0.0000000,90.0000000,0.0000000); //
	CreateDynamicObject(19448,318.4242900,1303.0185500,455.4490100,0.0000000,90.0000000,0.0000000); //
	CreateDynamicObject(19448,314.9442700,1303.0205100,455.4490100,0.0000000,90.0000000,0.0000000); //
	CreateDynamicObject(19448,317.9536400,1312.6544200,455.4490100,0.0000000,90.0000000,0.0000000); //
	CreateDynamicObject(19448,321.4554100,1312.6621100,455.4490100,0.0000000,90.0000000,0.0000000); //
	CreateDynamicObject(19448,324.9225800,1312.6536900,455.4490100,0.0000000,90.0000000,0.0000000); //
	CreateDynamicObject(19448,328.4162600,1312.6534400,455.4490100,0.0000000,90.0000000,0.0000000); //
	CreateDynamicObject(19448,331.9038700,1313.4808300,455.4490100,0.0000000,90.0000000,0.0000000); //
	CreateDynamicObject(19448,335.3825700,1313.4762000,455.4490100,0.0000000,90.0000000,0.0000000); //
	CreateDynamicObject(19448,338.8644400,1313.4841300,455.4490100,0.0000000,90.0000000,0.0000000); //
	CreateDynamicObject(19448,342.3677400,1313.4400600,455.4490100,0.0000000,90.0000000,0.0000000); //
	CreateDynamicObject(19448,339.4311500,1323.0577400,455.4490100,0.0000000,90.0000000,0.0000000); //
	CreateDynamicObject(19448,335.9300200,1323.1074200,455.4490100,0.0000000,90.0000000,0.0000000); //
	CreateDynamicObject(19448,332.4895000,1323.0972900,455.4490100,0.0000000,90.0000000,0.0000000); //
	CreateDynamicObject(19448,317.9582200,1322.2381600,455.4490100,0.0000000,90.0000000,0.0000000); //
	CreateDynamicObject(19448,321.4381100,1322.2851600,455.4490100,0.0000000,90.0000000,0.0000000); //
	CreateDynamicObject(19448,324.9380200,1322.2719700,455.4490100,0.0000000,90.0000000,0.0000000); //
	CreateDynamicObject(19448,328.4183700,1322.2628200,455.4490100,0.0000000,90.0000000,0.0000000); //
	CreateDynamicObject(19448,330.2915600,1322.9827900,455.4567300,0.0000000,90.0000000,0.0000000); //

	/*
	Objects converted: 140
	Vehicles converted: 0
	Vehicle models found: 0
	----------------------
	In the time this conversion took to finish 0.01 micro-fortnights have passed!
	*/


	// ATM'S
	
	CreateDynamicObject(2942,1928.6020500,-1784.6301300,13.1892900,0.0000000,0.0000000,89.8199900); //
	CreateDynamicObject(2942,2139.3933100,-1164.3564500,23.6123200,0.0000000,0.0000000,89.1000100); //
	CreateDynamicObject(2942,1332.9991500,-1243.9929200,13.2165100,0.0000000,0.0000000,89.0999800); //
	CreateDynamicObject(2942,2324.5207500,-1644.9679000,14.4560000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(2942,2482.0935100,-1958.7547600,13.1919700,0.0000000,0.0000000,180.5400100); //
	CreateDynamicObject(2942,2687.2426800,-1097.4024700,68.9188500,0.0000000,0.0000000,-90.2400100); //

	/*
	Objects converted: 6
	Vehicles converted: 0
	Vehicle models found: 0
	----------------------
	In the time this conversion took to finish the US national debt has risen by about $124.77!
	*/
	

	// Apartment 1 (one room, medium wealthy)
	
	CreateDynamicObject(19429,275.4097600,1356.0230700,345.6705000,0.0000000,-90.0000000,0.0000000); //
	CreateDynamicObject(19429,275.3959700,1352.8302000,345.6705000,0.0000000,-90.0000000,0.0000000); //
	CreateDynamicObject(19429,275.3895900,1354.4055200,345.6705000,0.0000000,-90.0000000,0.0000000); //
	CreateDynamicObject(19429,275.3906600,1357.6164600,345.6705000,0.0000000,-90.0000000,0.0000000); //
	CreateDynamicObject(19429,275.4006300,1359.1969000,345.6705000,0.0000000,-90.0000000,0.0000000); //
	CreateDynamicObject(19429,275.4132400,1360.7769800,345.6705000,0.0000000,-90.0000000,0.0000000); //
	CreateDynamicObject(19429,278.9161100,1360.7700200,345.6705000,0.0000000,-90.0000000,0.0000000); //
	CreateDynamicObject(19429,278.8971900,1359.1684600,345.6705000,0.0000000,-90.0000000,0.0000000); //
	CreateDynamicObject(19429,278.8974900,1357.5875200,345.6705000,0.0000000,-90.0000000,0.0000000); //
	CreateDynamicObject(19429,278.8873000,1356.0070800,345.6705000,0.0000000,-90.0000000,0.0000000); //
	CreateDynamicObject(19429,278.8773800,1354.4069800,345.6705000,0.0000000,-90.0000000,0.0000000); //
	CreateDynamicObject(19429,278.9261500,1352.8099400,345.6705000,0.0000000,-90.0000000,0.0000000); //
	CreateDynamicObject(19429,282.4035900,1352.8249500,345.6705000,0.0000000,-90.0000000,0.0000000); //
	CreateDynamicObject(19429,282.3886100,1354.4071000,345.6705000,0.0000000,-90.0000000,0.0000000); //
	CreateDynamicObject(19429,282.3655100,1355.9899900,345.6705000,0.0000000,-90.0000000,0.0000000); //
	CreateDynamicObject(19429,282.3806800,1357.5960700,345.6705000,0.0000000,-90.0000000,-0.0600000); //
	CreateDynamicObject(19429,282.3863200,1359.1563700,345.6705000,0.0000000,-90.0000000,-0.0600000); //
	CreateDynamicObject(19429,282.3916000,1360.7371800,345.6705000,0.0000000,-90.0000000,-0.0600000); //
	CreateDynamicObject(19439,282.5330500,1353.0238000,342.0510300,0.0000000,-90.0000000,0.0000000); //
	CreateDynamicObject(19427,284.0719600,1352.8150600,343.8593100,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19427,284.0934800,1355.9923100,343.8592800,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19427,284.0885900,1354.3914800,343.8592800,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19427,284.0948200,1357.5773900,343.8592500,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19427,284.0687000,1359.1789600,343.8592200,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19427,284.0403100,1360.7670900,343.8583100,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19427,283.1581700,1361.5607900,343.8621200,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(19427,281.5595700,1361.5551800,343.8674900,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(19427,279.9810800,1361.5441900,343.8542500,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(19427,278.5209000,1361.5507800,343.8542500,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(19427,277.0004900,1361.5476100,343.8542500,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(19427,275.4606000,1361.5418700,343.8542500,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(19427,274.0605200,1361.5764200,343.8542500,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(19427,273.5411400,1360.7703900,343.8583100,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19427,273.5288400,1359.2642800,343.8583100,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19427,273.5232200,1357.7440200,343.8583100,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19427,273.5344200,1356.2237500,343.8583100,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19427,273.5535600,1354.7033700,343.8583100,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19427,273.5534700,1353.2242400,343.8583100,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19427,273.5689100,1352.8441200,343.8583100,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19427,283.1831700,1352.1955600,343.8621200,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(19427,281.6626900,1352.1818800,343.8621200,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(19427,280.2207000,1352.2115500,343.8621200,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(19427,278.7005600,1352.2413300,343.8621200,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(19427,277.2008400,1352.2519500,343.8621200,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(19427,275.7407800,1352.2620800,343.8621200,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(19427,274.3807700,1352.2713600,343.8621200,0.0000000,0.0000000,90.0000000); //
	CreateDynamicObject(19439,279.0730300,1353.0262500,342.0510300,0.0000000,-90.0000000,0.0000000); //
	CreateDynamicObject(19439,275.6127900,1353.0346700,342.0510300,0.0000000,-90.0000000,-0.0600000); //
	CreateDynamicObject(19439,272.1125800,1353.0428500,342.0510300,0.0000000,-90.0000000,0.0000000); //
	CreateDynamicObject(19439,282.4557200,1354.6242700,342.0510300,0.0000000,-90.0000000,0.0000000); //
	CreateDynamicObject(19439,278.9640800,1354.6240200,342.0510300,0.0000000,-90.0000000,-0.0600000); //
	CreateDynamicObject(19439,275.4738200,1354.6384300,342.0510300,0.0000000,-90.0000000,0.0000000); //
	CreateDynamicObject(19439,272.0102800,1354.6259800,342.0579800,0.0000000,-90.0000000,0.0000000); //
	CreateDynamicObject(19439,282.4032900,1356.2308300,342.0510300,0.0000000,-90.0000000,0.0000000); //
	CreateDynamicObject(19439,278.9050600,1356.2233900,342.0510300,0.0000000,-90.0000000,-0.0600000); //
	CreateDynamicObject(19439,275.4165300,1356.2376700,342.0510300,0.0000000,-90.0000000,0.0000000); //
	CreateDynamicObject(19439,271.9673800,1356.2689200,342.0510300,0.0000000,-90.0000000,0.0000000); //
	CreateDynamicObject(19439,282.2764300,1361.0339400,342.0510300,0.0000000,-90.0000000,0.1200000); //
	CreateDynamicObject(19439,282.2894600,1357.8404500,342.0510300,0.0000000,-90.0000000,0.0000000); //
	CreateDynamicObject(19439,282.2981600,1359.4456800,342.0510300,0.0000000,-90.0000000,0.0000000); //
	CreateDynamicObject(19439,282.2764300,1361.0339400,342.0510300,0.0000000,-90.0000000,0.1200000); //
	CreateDynamicObject(19439,278.8133500,1357.8330100,342.0510300,0.0000000,-90.0000000,-0.0600000); //
	CreateDynamicObject(19439,278.8085000,1359.4268800,342.0510300,0.0000000,-90.0000000,-0.0600000); //
	CreateDynamicObject(19439,278.8051500,1361.0222200,342.0510300,0.0000000,-90.0000000,0.0000000); //
	CreateDynamicObject(8064,283.2028500,1361.3209200,338.6606100,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(19439,275.3172900,1357.8356900,342.0510300,0.0000000,-90.0000000,-0.0600000); //
	CreateDynamicObject(19439,275.3382000,1359.4405500,342.0510300,0.0000000,-90.0000000,-0.0600000); //
	CreateDynamicObject(19439,275.3108500,1361.0406500,342.0510300,0.0000000,-90.0000000,-0.0600000); //
	CreateDynamicObject(3072,280.6634500,1361.1066900,342.3407900,0.0000000,95.0000000,-4.6800000); //
	CreateDynamicObject(3072,281.9357000,1361.0567600,342.3407900,0.0000000,95.0000000,-4.0800000); //
	CreateDynamicObject(2614,273.6952800,1357.1379400,344.4748500,0.0000000,0.0000000,89.9399900); //
	CreateDynamicObject(8064,283.2028500,1361.3209200,349.8203400,180.1202200,-0.1800200,87.9000100); //
	CreateDynamicObject(2612,276.3496100,1361.3852500,344.0857200,0.0000000,0.0000000,-0.3000000); //
	CreateDynamicObject(1798,283.4421400,1355.7725800,342.1370500,0.0000000,0.0000000,180.2999900); //
	CreateDynamicObject(2093,282.2697400,1356.1322000,342.1369600,0.0000000,0.0000000,-54.4199600); //
	CreateDynamicObject(2028,282.8985000,1356.5133100,342.4250200,0.0000000,0.0000000,-2.7600000); //
	CreateDynamicObject(1841,283.7422800,1355.9638700,342.1384600,0.0000000,0.0000000,66.0000000); //
	CreateDynamicObject(1841,283.3016700,1356.4525100,343.3667600,0.0000000,0.0000000,66.0000000); //
	CreateDynamicObject(2627,283.3976700,1360.4420200,342.1373000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(2632,281.3157700,1359.9875500,342.1368400,0.0000000,0.0000000,89.4600400); //
	CreateDynamicObject(2827,283.0890800,1356.0031700,342.1555500,0.0000000,0.0000000,153.4799500); //
	CreateDynamicObject(2819,280.8616900,1353.8220200,342.1379400,0.0000000,0.0000000,-75.4800000); //
	CreateDynamicObject(2841,280.5217600,1353.9528800,342.1370200,0.0000000,0.0000000,88.1399900); //
	CreateDynamicObject(2277,283.2809100,1353.2651400,343.6878400,0.0000000,0.0000000,-90.7799000); //
	CreateDynamicObject(2270,283.4953900,1352.5637200,343.6599100,0.0000000,0.0000000,-89.6399600); //
	CreateDynamicObject(2268,283.4970100,1353.9613000,343.6599400,0.0000000,0.0000000,-90.1800200); //
	CreateDynamicObject(2257,281.0070500,1361.4661900,343.4989000,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(2114,283.7227200,1357.5814200,342.2776800,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(2239,281.0871600,1352.5651900,342.1382100,0.0000000,0.0000000,193.0799600); //
	CreateDynamicObject(1962,282.5082700,1352.3337400,344.2513400,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(1712,277.6919900,1355.1563700,342.1387300,0.0000000,0.0000000,-90.4800000); //
	CreateDynamicObject(2235,276.5502300,1353.9516600,342.1386400,0.0000000,0.0000000,90.2400300); //
	CreateDynamicObject(2689,283.9521200,1357.0087900,343.7696800,0.0000000,0.0000000,-90.4800000); //
	CreateDynamicObject(2704,283.9982000,1357.9571500,343.7933700,0.0000000,0.0000000,-90.2400600); //
	CreateDynamicObject(2705,283.9382000,1358.8895300,343.8169600,0.0000000,0.0000000,-92.7599800); //
	CreateDynamicObject(2681,279.6528000,1360.9604500,342.1369600,0.0000000,0.0000000,0.0000000); //
	CreateDynamicObject(2987,273.6740100,1354.4350600,343.8542500,-0.1799900,90.4199300,90.2399900); //
	CreateDynamicObject(2894,276.0646400,1354.1848100,342.6241800,0.0000000,0.0000000,92.0399900); //
	CreateDynamicObject(2849,276.0199900,1354.8466800,342.6241800,0.0000000,0.0000000,34.3200000); //
	CreateDynamicObject(1712,274.6833200,1356.5194100,342.1387300,0.0000000,0.0000000,-0.8400000); //
	CreateDynamicObject(1498,273.6098900,1361.0615200,342.2072100,0.0000000,0.0000000,268.6799300); //
	CreateDynamicObject(2295,278.3750000,1361.0312500,342.1384300,0.0000000,0.0000000,0.0000000); //

	/*
	Objects converted: 102
	Vehicles converted: 0
	Vehicle models found: 0
	----------------------
	In the time this conversion took to finish 0.01 micro-fortnights have passed!
	*/

	return 1;
}

public OnGameModeExit()
{
	//rash
	mysql_close();
	//rash
    TextDrawDestroy(ServerTimeTXT);
    FadeExit();
    
    for(new id = 1; id < sizeof(BusinessInfo); id++)
    {
        new file4[40];
	    format(file4, sizeof(file4), BPATH, id);
	    new INI:File = INI_Open(file4);
	    INI_SetTag(File,"data");
	    INI_WriteInt(File,"bOwned", BusinessInfo[id][bOwned]);
	    INI_WriteInt(File,"bPrice", BusinessInfo[id][bPrice]);
	    INI_WriteString(File,"bOwner", BusinessInfo[id][bOwner]);
	    INI_WriteInt(File,"bType", BusinessInfo[id][bType]);
	    INI_WriteInt(File,"bLocked", BusinessInfo[id][bLocked]);
	    INI_WriteInt(File,"bMoney", BusinessInfo[id][bMoney]);
	    INI_WriteFloat(File,"bEntranceX", BusinessInfo[id][bEntranceX]);
	    INI_WriteFloat(File,"bEntranceY", BusinessInfo[id][bEntranceY]);
	    INI_WriteFloat(File,"bEntranceZ", BusinessInfo[id][bEntranceZ]);
	    INI_WriteFloat(File,"bEntranceA", BusinessInfo[id][bEntranceA]);
	    INI_WriteFloat(File,"bExitX", BusinessInfo[id][bExitX]);
	    INI_WriteFloat(File,"bExitY", BusinessInfo[id][bExitY]);
	    INI_WriteFloat(File,"bExitZ", BusinessInfo[id][bExitZ]);
	    INI_WriteFloat(File,"bExitA", BusinessInfo[id][bExitA]);
	    INI_WriteInt(File,"bInt", BusinessInfo[id][bInt]);
	    INI_WriteInt(File,"bWorld", BusinessInfo[id][bWorld]);
	    INI_WriteInt(File,"bInsideInt", BusinessInfo[id][bInsideInt]);
	    INI_WriteInt(File,"bInsideWorld", BusinessInfo[id][bInsideWorld]);
	    INI_WriteString(File,"bName", BusinessInfo[id][bName]);
	    INI_Close(File);
    }
    
    for(new idz = 1; idz < sizeof(HouseInfo); idz++)
    {
        new file4[40];
	    format(file4, sizeof(file4), HPATH, idz);
	    new INI:File = INI_Open(file4);
	    INI_SetTag(File,"data");
	    INI_WriteInt(File,"hOwned", HouseInfo[idz][hOwned]);
	    INI_WriteInt(File,"hPrice", HouseInfo[idz][hPrice]);
	    INI_WriteString(File,"hOwner", HouseInfo[idz][hOwner]);
	    INI_WriteInt(File,"hLocked", HouseInfo[idz][hLocked]);
	    INI_WriteInt(File,"hMoney", HouseInfo[idz][hMoney]);
	    INI_WriteFloat(File,"hEntranceX", HouseInfo[idz][hEntranceX]);
	    INI_WriteFloat(File,"hEntranceY", HouseInfo[idz][hEntranceY]);
	    INI_WriteFloat(File,"hEntranceZ", HouseInfo[idz][hEntranceZ]);
	    INI_WriteFloat(File,"hEntranceA", HouseInfo[idz][hEntranceA]);
	    INI_WriteFloat(File,"hExitX", HouseInfo[idz][hExitX]);
	    INI_WriteFloat(File,"hExitY", HouseInfo[idz][hExitY]);
	    INI_WriteFloat(File,"hExitZ", HouseInfo[idz][hExitZ]);
	    INI_WriteFloat(File,"hExitA", HouseInfo[idz][hExitA]);
	    INI_WriteInt(File,"hInt", HouseInfo[idz][hInt]);
	    INI_WriteInt(File,"hWorld", HouseInfo[idz][hWorld]);
	    INI_WriteInt(File,"hInsideInt", HouseInfo[idz][hInsideInt]);
	    INI_WriteInt(File,"hInsideWorld", HouseInfo[idz][hInsideWorld]);
	    INI_Close(File);
    }
    
	KillTimer(maintimer);
	KillTimer(speedotimer);
	KillTimer(savetimer);
	//TextDrawDestroy(SpeedoBox);
	for(new i=0; i < MAX_PLAYERS; i++)
	{
		if(IsPlayerConnected(i))
		{
			OnPlayerDisconnect(i, 1);
		}
	}
	for(new i=1; i < MAX_DVEHICLES; i++)
	{
		if(VehicleCreated[i])
		{
			DestroyVehicle(VehicleID[i]);
			if(VehicleCreated[i] == VEHICLE_DEALERSHIP)
			{
				Delete3DTextLabel(VehicleLabel[i]);
			}
		}
	}
	for(new i=1; i < MAX_DEALERSHIPS; i++)
	{
		if(DealershipCreated[i])
		{
			Delete3DTextLabel(DealershipLabel[i]);
		}
	}
	for(new i=1; i < MAX_FUEL_STATIONS; i++)
	{
		if(FuelStationCreated[i])
		{
			Delete3DTextLabel(FuelStationLabel[i]);
		}
	}
	return 1;
}


/* Animations
*/

CMD:crack(playerid, params[])
{
    new
	give[3];

    if(sscanf(params, "s[3]", give)) return SendClientMessage(playerid, COLOR_GREY, "[Usage]: /crack [1-2]");
    if(!strcmp(give, "1", true))
    {
   		LoopingAnim(playerid, "CRACK", "crckdeth2", 4.0, 1, 0, 0, 0, 0,1);
    }
    else if(!strcmp(give, "2", true))
    {
   		LoopingAnim(playerid, "CRACK", "crckidle1", 4.0, 1, 0, 0, 0, 0,1);
    }
    return 1;
}

CMD:chat(playerid, params[])
{
	LoopingAnim(playerid,"MISC","IDLE_CHAT_02",2.0,1,0,0,1,1,1);
	return 1;
}

CMD:hike(playerid, params[])
{
	OnePlayAnim(playerid,"PED","idle_taxi",3.0,0,0,0,0,0,1);
	return 1;
}

CMD:caract(playerid, params[])
{
	LoopingAnim(playerid,"PED","TAP_HAND",4.0,1,0,0,0,0,1);
	return 1;
}

CMD:give(playerid, params[])
{
	OnePlayAnim(playerid,"KISSING","gift_give",3.0,0,0,0,0,0,1);
	return 1;
}

CMD:pull(playerid, params[])
{
	OnePlayAnim(playerid,"AIRPORT","thrw_barl_thrw ",3.0,0,0,0,0,0,1);
	return 1;
}

CMD:face(playerid, params[])
{
	LoopingAnim(playerid,"PED","facanger",3.0,1,1,1,1,1,1);
	return 1;
}

CMD:endchat(playerid, params[])
{
	OnePlayAnim(playerid,"PED","endchat_01",8.0,0,0,0,0,0,1);
	return 1;
}

CMD:show(playerid, params[])
{
	LoopingAnim(playerid,"ON_LOOKERS","point_loop",3.0,1,0,0,0,0,1);
	return 1;
}

CMD:shoutanim(playerid, params[])
{
	BackAnim(playerid,"ON_LOOKERS","shout_loop",3.0,1,0,0,0,0,6,1);
	return 1;
}

CMD:look(playerid, params[])
{
	LoopingAnim(playerid,"ON_LOOKERS","lkup_loop",3.0,1,0,0,0,0,1);
	return 1;
}

CMD:drunk(playerid, params[])
{
	LoopingAnim(playerid,"PED","WALK_DRUNK",4.1,1,1,1,1,1,1);
	return 1;
}

CMD:sit(playerid, params[])
{
    new
	give[5];

    if(sscanf(params, "s[5]", give)) return SendClientMessage(playerid, COLOR_GREY, "[Usage]: /sit [1-4]");
    if(!strcmp(give, "1", true))
    {
		BackAnim(playerid,"PED","SEAT_down",4.1,0,1,1,1,0,8,1);
    }
    else if(!strcmp(give, "2", true))
    {
		BackAnim(playerid,"BEACH","ParkSit_M_loop",4.1,0,1,1,1,0,8,1);
    }
    else if(!strcmp(give, "3", true))
    {
		BackAnim(playerid,"MISC","SEAT_LR",4.1,0,1,1,1,0,8,1);
    }
    else if(!strcmp(give, "4", true))
    {
		BackAnim(playerid,"MISC","Seat_talk_02",4.1,0,1,1,1,0,8,1);
    }
	return 1;
}

CMD:scratch(playerid, params[])
{
    ApplyAnimation(playerid, "MISC", "Scratchballs_01", 4.1, 1, 1, 1, 1, 1, 1);
    return 1;
}

CMD:reload(playerid, params[])
{
    ApplyAnimation(playerid, "COLT45", "colt45_reload", 4.1, 0, 1, 1, 1, 1, 1);
    return 1;
}

CMD:injured(playerid, params[])
{
	LoopingAnim(playerid, "SWEET", "Sweet_injuredloop", 4.0, 1, 0, 0, 0, 0,1);
	return 1;
}

CMD:dive(playerid, params[])
{
	ApplyAnimation(playerid, "DODGE", "Cover_Dive_01", 4.0, 0, 0, 0, 0, 0,1);
 	SetTimerEx("DiveAnim", 1000, false, "i", playerid);
	return 1;
}


CMD:sign(playerid, params[])
{
    new
	give[5];

    if(sscanf(params, "s[5]", give)) return SendClientMessage(playerid, COLOR_GREY, "[Usage]: /sign [1-4]");
    if(!strcmp(give, "1", true))
    {
    	ApplyAnimation(playerid, "GHANDS", "gsign2", 4.1, 1, 1, 1, 1, 1, 1);
    }
    else if(!strcmp(give, "2", true))
    {
    	ApplyAnimation(playerid, "GHANDS", "gsign3", 4.1, 1, 1, 1, 1, 1, 1);
    }
    else if(!strcmp(give, "3", true))
    {
        ApplyAnimation(playerid, "GHANDS", "gsign5", 4.1, 1, 1, 1, 1, 1, 1);
    }
    else if(!strcmp(give, "4", true))
    {
        ApplyAnimation(playerid, "GHANDS", "gsign4LH", 4.1, 1, 1, 1, 1, 1, 1);
    }
    return 1;
}

CMD:chill(playerid, params[])
{
    new
	give[4];

    if(sscanf(params, "s[4]", give)) return SendClientMessage(playerid, COLOR_GREY, "[Usage]: /chill [1-3]");
    if(!strcmp(give, "1", true))
    {
    	ApplyAnimation(playerid, "RAPPING", "RAP_A_Loop", 4.1, 1, 1, 1, 1, 1, 1);
    }
    else if(!strcmp(give, "2", true))
    {
    	ApplyAnimation(playerid, "RAPPING", "RAP_A_OUT", 4.1, 0, 1, 1, 1, 1, 1);
    }
    else if(!strcmp(give, "3", true))
    {
        ApplyAnimation(playerid, "RAPPING", "RAP_B_Loop", 4.1, 1, 1, 1, 1, 1, 1);
    }
    return 1;
}

CMD:gwalk(playerid, params[])
{
    new
	give[3];

    if(sscanf(params, "s[3]", give)) return SendClientMessage(playerid, COLOR_GREY, "[Usage]: /gwalk [1-2]");
    if(!strcmp(give, "1", true))
    {
        ApplyAnimation(playerid, "PED", "WALK_gang1", 4.1, 1, 1, 1, 1, 1, 1);
    }
    else if(!strcmp(give, "2", true))
    {
        ApplyAnimation(playerid, "PED", "WALK_gang2", 4.1, 1, 1, 1, 1, 1, 1);
    }
    return 1;
}

CMD:grafitti(playerid, params[])
{
    new
	give[3];

    if(sscanf(params, "s[3]", give)) return SendClientMessage(playerid, COLOR_GREY, "[Usage]: /grafitti [1-2]");
    if(!strcmp(give, "1", true))
    {
        ApplyAnimation(playerid, "GRAFFITI", "graffiti_Chkout", 4.1, 1, 1, 1, 1, 1, 1);
    }
    else if(!strcmp(give, "2", true))
    {
        ApplyAnimation(playerid, "GRAFFITI", "spraycan_fire", 4.1, 1, 1, 1, 1, 1, 1);
    }
    return 1;
}

CMD:camera(playerid, params[])
{
    new
	give[4];

    if(sscanf(params, "s[4]", give)) return SendClientMessage(playerid, COLOR_GREY, "[Usage]: /camera [1-3]");
    if(!strcmp(give, "1", true))
    {
        ApplyAnimation(playerid, "CAMERA", "camcrch_cmon", 4.1, 0, 1, 1, 1, 1, 1);
    }
    else if(!strcmp(give, "2", true))
    {
        ApplyAnimation(playerid, "CAMERA", "camcrch_idleloop ", 4.1, 0, 1, 1, 1, 1, 1);
    }
    else if(!strcmp(give, "3", true))
    {
        ApplyAnimation(playerid, "CAMERA", "camstnd_to_camcrch", 4.1, 0, 1, 1, 1, 1, 1);
    }
    return 1;
}

CMD:rap(playerid, params[])
{
	LoopingAnim(playerid,"RAPPING","RAP_A_Loop",4.0,1,0,0,0,0,1);
	return 1;
}

CMD:think(playerid, params[])
{
	ApplyAnimation(playerid, "COP_AMBIENT", "Coplook_think", 4.1, 0, 1, 1, 1, 1, 1);
	return 1;
}

CMD:box(playerid, params[])
{
	LoopingAnim(playerid,"GYMNASIUM","GYMshadowbox",4.0,1,1,1,1,0,1);
	return 1;
}

CMD:tired(playerid, params[])
{
	LoopingAnim(playerid,"PED","IDLE_tired",3.0,1,0,0,0,0,1);
	return 1;
}

CMD:cop(playerid, params[])
{
	LoopingAnim(playerid,"ped", "ARRESTgun", 4.0, 0, 1, 1, 1, -1,1);
	return 1;
}

CMD:stance(playerid, params[])
{
    new
	give[3];

    if(sscanf(params, "s[3]", give)) return SendClientMessage(playerid, COLOR_GREY, "[Usage]: /stance [1-2]");
    if(!strcmp(give, "1", true))
    {
   		LoopingAnim(playerid,"DEALER","DEALER_IDLE",4.0,1,0,0,0,0,1);
    }
	else if(!strcmp(give, "2", true))
    {
		OnePlayAnim(playerid, "BAR", "BARman_idle", 2.0, 0, 0, 0, 0, 0,1);
    }
	return 1;
}

CMD:bar(playerid, params[])
{
    new
	give[3];

    if(sscanf(params, "s[3]", give)) return SendClientMessage(playerid, COLOR_GREY, "[Usage]: /bar [1-2]");
    if(!strcmp(give, "1", true))
    {
		OnePlayAnim(playerid, "BAR", "Barserve_bottle", 2.0, 0, 0, 0, 0, 0,1);
    }
	else if(!strcmp(give, "2", true))
    {
		OnePlayAnim(playerid, "BAR", "Barserve_give", 2.0, 0, 0, 0, 0, 0,1);
    }
	return 1;
}

CMD:bat(playerid, params[])
{
    new
	give[4];

    if(sscanf(params, "s[4]", give)) return SendClientMessage(playerid, COLOR_GREY, "[Usage]: /bat [1-3]");
    if(!strcmp(give, "1", true))
    {
		OnePlayAnim(playerid, "BASEBALL", "Bat_IDLE", 2.0, 0, 0, 0, 0, 0,1);
    }
    else if(!strcmp(give, "2", true))
    {
		OnePlayAnim(playerid, "CRACK", "Bbalbat_Idle_01", 2.0, 0, 0, 0, 0, 0,1);
    }
    else if(!strcmp(give, "3", true))
    {
		OnePlayAnim(playerid, "CRACK", "Bbalbat_Idle_02", 2.0, 0, 0, 0, 0, 0,1);
    }
	return 1;
}

CMD:lean(playerid, params[])
{
	LoopingAnim(playerid,"GANGS","leanIDLE",4.0,0,1,1,1,0,1);
	return 1;
}

CMD:dance(playerid, params[])
{
    new
	give[7];

    if(sscanf(params, "s[7]", give)) return SendClientMessage(playerid, COLOR_GREY, "[Usage]: /dance [1-6]");
    if(!strcmp(give, "1", true))
    {
   		SetPlayerSpecialAction(playerid,SPECIAL_ACTION_DANCE1);
    }
    else if(!strcmp(give, "2", true))
    {
        ApplyAnimation(playerid, "DANCE", "dnce_M_a", 4.1, 1, 1, 1, 1, 1, 1);
    }
    else if(!strcmp(give, "3", true))
    {
        ApplyAnimation(playerid, "DANCE", "dnce_M_b", 4.1, 1, 1, 1, 1, 1, 1);
    }
    else if(!strcmp(give, "4", true))
    {
        ApplyAnimation(playerid, "DANCE", "dnce_M_c", 4.1, 1, 1, 1, 1, 1, 1);
    }
    else if(!strcmp(give, "5", true))
    {
        ApplyAnimation(playerid, "DANCE", "dnce_M_d", 4.1, 1, 1, 1, 1, 1, 1);
    }
    else if(!strcmp(give, "6", true))
    {
        ApplyAnimation(playerid, "DANCE", "dnce_M_e", 4.1, 1, 1, 1, 1, 1, 1);
    }
    return 1;
}

CMD:kiss(playerid, params[])
{
	OnePlayAnim(playerid, "BD_Fire", "grlfrd_kiss_03", 2.0, 0, 0, 0, 0, 0,1);
	return 1;
}

CMD:cpr(playerid, params[])
{
    ApplyAnimation(playerid, "MEDIC", "CPR", 4.1, 0, 1, 1, 1, 1, 1);
    return 1;
}

CMD:handsup(playerid, params[])
{
	SetPlayerSpecialAction(playerid,SPECIAL_ACTION_HANDSUP);
	return 1;
}

CMD:bomb(playerid, params[])
{
	ClearAnimations(playerid);
	OnePlayAnim(playerid, "BOMBER", "BOM_Plant", 4.0, 0, 0, 0, 0, 0,1); // Place Bomb
	return 1;
}

CMD:getarrested(playerid, params[])
{
	LoopingAnim(playerid,"ped", "ARRESTgun", 4.0, 0, 1, 1, 1, -1,1); // Gun Arrest
	return 1;
}

CMD:laugh(playerid, params[])
{
	OnePlayAnim(playerid, "RAPPING", "Laugh_01", 4.0, 0, 0, 0, 0, 0,1); // Laugh
	return 1;
}
	
CMD:lookout(playerid, params[])
{
	OnePlayAnim(playerid, "SHOP", "ROB_Shifty", 4.0, 0, 0, 0, 0, 0,1); // Rob Lookout
	return 1;
}

CMD:aim(playerid, params[])
{
	LoopingAnim(playerid, "SHOP", "ROB_Loop_Threat", 4.0, 1, 0, 0, 0, 0,1); // Rob
	return 1;
}

CMD:crossarms(playerid, params[])
{
	LoopingAnim(playerid, "COP_AMBIENT", "Coplook_loop", 4.0, 0, 1, 1, 1, -1,1); // Arms crossed
	return 1;
}

CMD:car(playerid, params[])
{
    new
	give[4];

    if(sscanf(params, "s[4]", give)) return SendClientMessage(playerid, COLOR_GREY, "[Usage]: /car [1-3]");
    if(!strcmp(give, "1", true))
    {
   		LoopingAnim(playerid,"CAR","Fixn_Car_Loop", 4.0, 1, 0, 0, 0, 0,1);
    }
    else if(!strcmp(give, "2", true))
    {
        ApplyAnimation(playerid, "CAR", "Fixn_Car_Out", 4.1, 1, 1, 1, 1, 1, 1);
    }
    else if(!strcmp(give, "3", true))
    {
        ApplyAnimation(playerid, "CAR", "flag_drop", 4.1, 1, 1, 1, 1, 1, 1);
    }
    return 1;
}

CMD:lay(playerid, params[])
{
    new
	give[4];

    if(sscanf(params, "s[4]", give)) return SendClientMessage(playerid, COLOR_GREY, "[Usage]: /lay [1-3]");
    if(!strcmp(give, "1", true))
    {
   		LoopingAnim(playerid,"BEACH","bather", 4.0, 1, 0, 0, 0, 0,1);
    }
    else if(!strcmp(give, "2", true))
    {
        LoopingAnim(playerid,"BEACH","SitnWait_loop_W", 4.0, 1, 0, 0, 0, 0,1);
    }
    else if(!strcmp(give, "3", true))
    {
        LoopingAnim(playerid,"CRACK","crckidle4", 4.0, 1, 0, 0, 0, 0,1);
    }
    return 1;
}

CMD:what(playerid, params[])
{
    new
	give[3];

    if(sscanf(params, "s[3]", give)) return SendClientMessage(playerid, COLOR_GREY, "[Usage]: /what [1-2]");
    if(!strcmp(give, "1", true))
    {
   		LoopingAnim(playerid,"benchpress","gym_bp_celebrate", 4.0, 1, 0, 0, 0, 0,1);
    }
    else if(!strcmp(give, "2", true))
    {
        ApplyAnimation(playerid, "BEACH", "SitnWait_loop_W", 4.1, 1, 1, 1, 1, 1, 1);
    }
    return 1;
}

CMD:hide(playerid, params[])
{

	LoopingAnim(playerid, "ped", "cower", 3.0, 1, 0, 0, 0, 0,1);
	return 1;
}

CMD:vomit(playerid, params[])
{
	OnePlayAnim(playerid, "FOOD", "EAT_Vomit_P", 3.0, 0, 0, 0, 0, 0,1); // Vomit BAH!
	return 1;
}

CMD:eat(playerid, params[])
{
	OnePlayAnim(playerid, "FOOD", "EAT_Burger", 3.0, 0, 0, 0, 0, 0,1); // Eat Burger
	return 1;
}

CMD:wave(playerid, params[])
{
	LoopingAnim(playerid, "ON_LOOKERS", "wave_loop", 4.0, 1, 0, 0, 0, 0,1);
	return 1;
}

CMD:chant(playerid, params[])
{
	LoopingAnim(playerid,"RIOT","RIOT_CHANT",4.0,1,1,1,1,0,1);
	return 1;
}

CMD:slap(playerid, params[])
{
	OnePlayAnim(playerid, "SWEET", "sweet_ass_slap", 4.0, 0, 0, 0, 0, 0,1);
	return 1;
}

CMD:deal(playerid, params[])
{
	OnePlayAnim(playerid, "DEALER", "DEALER_DEAL", 4.0, 0, 0, 0, 0, 0,1); // Deal Drugs
 	return 1;
}

CMD:fuck(playerid, params[])
{
	OnePlayAnim(playerid,"PED","fucku",4.0,0,0,0,0,0,1);
	return 1;
}

CMD:taichi(playerid, params[])
{
	LoopingAnim(playerid,"PARK","Tai_Chi_Loop",4.0,1,0,0,0,1,1);
	return 1;
}

CMD:chairsit(playerid, params[])
{
	LoopingAnim(playerid,"BAR","dnk_stndF_loop",4.0,1,0,0,0,1,1);
   	return 1;
}

CMD:stopanim(playerid, params[])
{
	ClearAnimations(playerid);
	return 1;
}

/* Vehicle System
*/

CMD:fix(playerid, params[])
{
	if(GetPlayerState(playerid) != PLAYER_STATE_DRIVER) return SendClientMessage(playerid, COLOR_RED, "You are not driving a vehicle!");
	new vehicleid = GetPlayerVehicleID(playerid);
	RepairVehicle(vehicleid);
	return 1;
}

CMD:flip(playerid, params[])
{
	if(GetPlayerState(playerid) != PLAYER_STATE_DRIVER) return SendClientMessage(playerid, COLOR_RED, "You are not driving a vehicle!");
	new vehicleid = GetPlayerVehicleID(playerid);
	new Float:angle;
	GetVehicleZAngle(vehicleid, angle);
	SetVehicleZAngle(vehicleid, angle);
	return 1;
}

CMD:tow(playerid, params[])
{
	if(GetPlayerState(playerid) != PLAYER_STATE_DRIVER) return SendClientMessage(playerid, COLOR_RED, "You are not driving a vehicle!");
	new vehicleid = GetPlayerVehicleID(playerid);
	if(IsTrailerAttachedToVehicle(vehicleid))
	{
		DetachTrailerFromVehicle(vehicleid);
		return 1;
	}
	new Float:x, Float:y, Float:z;
	new Float:dist, Float:closedist=8, closeveh;
	for(new i=1; i < MAX_VEHICLES; i++)
	{
		if(i != vehicleid && GetVehiclePos(i, x, y, z))
		{
			dist = GetPlayerDistanceFromPoint(playerid, x, y, z);
			if(dist < closedist)
			{
				closedist = dist;
				closeveh = i;
			}
		}
	}
	if(!closeveh) return SendClientMessage(playerid, COLOR_RED, "You are not close to a vehicle!");
	AttachTrailerToVehicle(closeveh, vehicleid);
	return 1;
}

CMD:kph(playerid, params[])
{
	SetPVarInt(playerid, "Speedo", 0);
	SendClientMessage(playerid, COLOR_GOLD, "Speedometer units set to KPH.");
	return 1;
}

CMD:mph(playerid, params[])
{
	SetPVarInt(playerid, "Speedo", 1);
	SendClientMessage(playerid, COLOR_GOLD, "Speedometer units set to MPH.");
	return 1;
}

CMD:eject(playerid, params[])
{
	if(GetPlayerState(playerid) != PLAYER_STATE_DRIVER) return SendClientMessage(playerid, COLOR_RED, "You are not driving a vehicle!");
	new pid, msg[128];
	if(sscanf(params, "u", pid)) return SendClientMessage(playerid, COLOR_GREY, "[Usage]: /eject [player]");
	if(!IsPlayerConnected(pid)) return SendClientMessage(playerid, COLOR_RED, "Invalid player!");
	new vehicleid = GetPlayerVehicleID(playerid);
	if(!IsPlayerInVehicle(pid, vehicleid)) return SendClientMessage(playerid, COLOR_RED, "Player is not in your vehicle!");
	RemovePlayerFromVehicle(pid);
	format(msg, sizeof(msg), "%s (%d) has ejected youfrom the vehicle.", PlayerName(playerid), playerid);
	SendClientMessage(pid, COLOR_GOLD, msg);
	format(msg, sizeof(msg), "You have ejected %s (%d) from your vehicle.", PlayerName(pid), pid);
	SendClientMessage(playerid, COLOR_GOLD, msg);
	return 1;
}

CMD:ejectall(playerid, params[])
{
	if(GetPlayerState(playerid) != PLAYER_STATE_DRIVER) return SendClientMessage(playerid, COLOR_RED, "You are not driving a vehicle!");
	new vehicleid = GetPlayerVehicleID(playerid);
	new msg[128];
	format(msg, sizeof(msg), "Vehicle driver %s (%d) has ejected you", PlayerName(playerid), playerid);
	for(new i=0; i < MAX_PLAYERS; i++)
	{
		if(IsPlayerConnected(i) && i != playerid && IsPlayerInVehicle(i, vehicleid))
		{
			RemovePlayerFromVehicle(i);
			SendClientMessage(i, COLOR_WHITE, msg);
		}
	}
	SendClientMessage(playerid, COLOR_GOLD, "You have ejected all passengers.");
	return 1;
}

CMD:clearmods(playerid, params[])
{
	if(GetPlayerState(playerid) != PLAYER_STATE_DRIVER) return SendClientMessage(playerid, COLOR_RED, "You are not driving a vehicle!");
	new vehicleid = GetPlayerVehicleID(playerid);
	new id = GetVehicleID(vehicleid);
	if(GetPlayerVehicleAccess(playerid, id) < 2)
		return SendClientMessage(playerid, COLOR_RED, "This is not your vehicle!");
	for(new i=0; i < sizeof(VehicleMods[]); i++)
	{
		RemoveVehicleComponent(VehicleID[id], GetVehicleComponentInSlot(VehicleID[id], i));
		VehicleMods[id][i] = 0;
	}
	VehiclePaintjob[id] = 255;
	ChangeVehiclePaintjob(VehicleID[id], 255);
	SaveVehicle(id);
	SendClientMessage(playerid, COLOR_GOLD, "You have removed all modifications from your vehicle.");
	return 1;
}

CMD:trackcar(playerid, params[])
{
	if(TrackCar[playerid])
	{
		TrackCar[playerid] = 0;
		DisablePlayerCheckpoint(playerid);
		SendClientMessage(playerid, COLOR_GOLD, "You are not tracking your vehicle anymore.");
		return 1;
	}
	new playername[24];
	GetPlayerName(playerid, playername, sizeof(playername));
	new info[256], bool:found;
	for(new i=1; i < MAX_DVEHICLES; i++)
	{
		if(VehicleCreated[i] == VEHICLE_PLAYER && strcmp(VehicleOwner[i], playername) == 0)
		{
			found = true;
			format(info, sizeof(info), "%sID: %d  Name: %s\n", info, i, VehicleNames[VehicleModel[i]-400]);
		}
	}
	if(!found) return SendClientMessage(playerid, COLOR_LIGHTRED, "You don't have any vehicles!");
	ShowPlayerDialog(playerid, DIALOG_FINDVEHICLE, DIALOG_STYLE_LIST, "Find Your Vehicle", info, "Find", "Cancel");
	return 1;
}

CMD:v(playerid, params[])
{
	if(GetPlayerState(playerid) != PLAYER_STATE_DRIVER) return SendClientMessage(playerid, COLOR_RED, "You are not driving a vehicle!");
	new vehicleid = GetPlayerVehicleID(playerid);
	if(IsBicycle(vehicleid)) return SendClientMessage(playerid, COLOR_LIGHTRED, "You are not driving a vehicle!");
	new id = GetVehicleID(vehicleid);
	if(GetPlayerVehicleAccess(playerid, id) < 1)
		return SendClientMessage(playerid, COLOR_LIGHTRED, "* You don't have the keys for this vehicle!");
	SetPVarInt(playerid, "DialogValue1", id);
	ShowDialog(playerid, DIALOG_VEHICLE);
	return 1;
}

CMD:sellv(playerid, params[])
{
	new pid, id, price, msg[128];
	if(sscanf(params, "udd", pid, id, price)) return SendClientMessage(playerid, COLOR_GREY, "USAGE: /sellv [player] [vehicleid] [price]");
	if(!IsPlayerConnected(pid)) return SendClientMessage(playerid, COLOR_RED, "Invalid player!");
	if(GetPlayerVehicleAccess(playerid, id) < 2)
		return SendClientMessage(playerid, COLOR_LIGHTRED, "* You are not the owner of this vehicle.");
	if(price < 1) return SendClientMessage(playerid, COLOR_LIGHTRED, "Invalid price.");
	if(!PlayerToPlayer(playerid, pid, 10.0)) return SendClientMessage(playerid, COLOR_LIGHTRED, "Player is too far away.");
	SetPVarInt(pid, "DialogValue1", playerid);
	SetPVarInt(pid, "DialogValue2", id);
	SetPVarInt(pid, "DialogValue3", price);
	ShowDialog(pid, DIALOG_VEHICLE_SELL);
	format(msg, sizeof(msg), "You have offered %s (%d) to buy your vehicle for $%d.", PlayerName(pid), pid, price);
	SendClientMessage(playerid, COLOR_GOLD, msg);
	return 1;
}

CMD:givecarkeys(playerid, params[])
{
	new pid, id, msg[128];
	if(sscanf(params, "ud", pid, id)) return SendClientMessage(playerid, COLOR_GREY, "USAGE: /givecarkeys [player] [vehicleid]");
	if(!IsPlayerConnected(pid)) return SendClientMessage(playerid, COLOR_LIGHTRED, "Invalid player.");
	if(!IsValidVehicle(id)) return SendClientMessage(playerid, COLOR_LIGHTRED, "Invalid vehicleid.");
	if(GetPlayerVehicleAccess(playerid, id) < 2)
		return SendClientMessage(playerid, COLOR_LIGHTRED, "You are not the owner of this vehicle.");
	if(!PlayerToPlayer(playerid, pid, 10.0)) return SendClientMessage(playerid, COLOR_LIGHTRED, "Player is too far away.");
	SetPVarInt(pid, "CarKeys", id);
	format(msg, sizeof(msg), "You have given your car keys to %s (%d).", PlayerName(pid), pid);
	SendClientMessage(playerid, COLOR_GOLD, msg);
	format(msg, sizeof(msg), "%s (%d) has given you his extra-pair of his vehicle keys.", PlayerName(playerid), playerid);
	SendClientMessage(pid, COLOR_GOLD, msg);
	return 1;
}

CMD:vlock(playerid, params[])
{
	new vehicleid;
	if(GetPlayerState(playerid) == PLAYER_STATE_DRIVER)
	{
		vehicleid = GetPlayerVehicleID(playerid);
	}
	else
	{
		vehicleid = GetClosestVehicle(playerid);
		if(!PlayerToVehicle(playerid, vehicleid, 5.0)) vehicleid = 0;
 }
	if(!vehicleid) return SendClientMessage(playerid, COLOR_LIGHTRED, "You are not close to a vehicle.");
	new id = GetVehicleID(vehicleid);
	if(!IsValidVehicle(id)) return SendClientMessage(playerid, COLOR_LIGHTRED, "You don't have the keys for this vehicle.");
	if(GetPlayerVehicleAccess(playerid, id) < 2)
		return SendClientMessage(playerid, COLOR_LIGHTRED, "You don't have the keys for this vehicle");
	GetVehicleParamsEx(vehicleid, engine, lights, alarm, doors, bonnet, boot, objective);
	if(doors == 1)
	{
		doors = 0;
		VehicleLock[id] = 0;
		GameTextForPlayer(playerid, "~w~vehicle ~g~unlocked", 3000, 6);
  		PlayerPlaySound(playerid, 1145, 0.0, 0.0, 0.0);
	}
	else
	{
		doors = 1;
		VehicleLock[id] = 1;
		GameTextForPlayer(playerid, "~w~vehicle ~r~locked", 3000, 6);
  		PlayerPlaySound(playerid, 1145, 0.0, 0.0, 0.0);
	}
	SetVehicleParamsEx(vehicleid, engine, lights, alarm, doors, bonnet, boot, objective);
	SaveVehicle(id);
	return 1;
}

CMD:valarm(playerid, params[])
{
	new vehicleid;
	if(GetPlayerState(playerid) == PLAYER_STATE_DRIVER)
	{
		vehicleid = GetPlayerVehicleID(playerid);
	}
	else
	{
		vehicleid = GetClosestVehicle(playerid);
		if(!PlayerToVehicle(playerid, vehicleid, 5.0)) vehicleid = 0;
	}
	if(!vehicleid) return SendClientMessage(playerid, COLOR_LIGHTRED, "You are not close to a vehicle.");
	new id = GetVehicleID(vehicleid);
	if(!IsValidVehicle(id)) return SendClientMessage(playerid, COLOR_LIGHTRED, "You don't have the keys for this vehicle.");
	if(GetPlayerVehicleAccess(playerid, id) < 2)
		return SendClientMessage(playerid, COLOR_LIGHTRED, "You don't have the keys for this vehicle.");
	if(VehicleSecurity[vehicleid] == 0)
	{
		VehicleSecurity[vehicleid] = 1;
		VehicleAlarm[id] = 1;
		GameTextForPlayer(playerid, "~g~alarm on", 3000, 6);
	}
	else
	{
		ToggleAlarm(vehicleid, VEHICLE_PARAMS_OFF);
		VehicleSecurity[vehicleid] = 0;
		VehicleAlarm[id] = 0;
		GameTextForPlayer(playerid, "~r~alarm off", 3000, 6);
	}
	SaveVehicle(id);
	return 1;
}

CMD:trunk(playerid, params[])
{
	new vehicleid = GetClosestVehicle(playerid);
	if(!PlayerToVehicle(playerid, vehicleid, 5.0)) vehicleid = 0;
	if(!vehicleid || IsBicycle(vehicleid) || IsPlayerInAnyVehicle(playerid))
		return SendClientMessage(playerid, COLOR_LIGHTRED, "You are not close to a vehicle.");
	new id = GetVehicleID(vehicleid);
	if(!IsValidVehicle(id)) return SendClientMessage(playerid, COLOR_LIGHTRED, "You don't have the keys for this vehicle.");
	if(GetPlayerVehicleAccess(playerid, id) < 2)
		return SendClientMessage(playerid, COLOR_LIGHTRED, "You don't have the keys for this vehicle.");
	ToggleBoot(vehicleid, VEHICLE_PARAMS_ON);
	SetPVarInt(playerid, "DialogValue1", id);
	ShowDialog(playerid, DIALOG_TRUNK);
	return 1;
}

CMD:refuel(playerid, params[])
{
	for(new i=1; i < MAX_FUEL_STATIONS; i++)
	{
		if(FuelStationCreated[i])
		{
			if(IsPlayerInRangeOfPoint(playerid, 15.0, FuelStationPos[i][0], FuelStationPos[i][1], FuelStationPos[i][2]))
			{
				SetPVarInt(playerid, "FuelStation", i);
				ShowDialog(playerid, DIALOG_FUEL);
				return 1;
			}
		}
	}
	SendClientMessage(playerid, COLOR_LIGHTRED, "You are not in a fuel station.");
	return 1;
}

CMD:rtc(playerid, params[])
{
	if(!IsAdmin(playerid, 1)) return SendClientMessage(playerid, COLOR_GREY, "You are unauthorized to use that command.");
	if(!IsPlayerInAnyVehicle(playerid)) return SendClientMessage(playerid, COLOR_LIGHTRED, "You are not in a vehicle.");
	SetVehicleToRespawn(GetPlayerVehicleID(playerid));
	SendClientMessage(playerid, COLOR_GOLD, "Vehicle respawned.");
	return 1;
}

CMD:rac(playerid, params[])
{
	if(!IsAdmin(playerid, 1)) return SendClientMessage(playerid, COLOR_LIGHTRED, "You are not admin.");
	new bool:vehicleused[MAX_VEHICLES];
	for(new i=0; i < MAX_PLAYERS; i++)
	{
		if(IsPlayerConnected(i) && IsPlayerInAnyVehicle(i))
		{
			vehicleused[GetPlayerVehicleID(i)] = true;
		}
	}
	for(new i=1; i < MAX_VEHICLES; i++)
	{
		if(!vehicleused[i])
		{
			SetVehicleToRespawn(i);
		}
	}
	new msg[128];
	format(msg, sizeof(msg), "AdmCmd: %s (%d) has respawned all unoccupied vehicles.", PlayerName(playerid), playerid);
	SendClientMessageToAll(COLOR_LIGHTRED, msg);
	return 1;
}

CMD:setfuel(playerid, params[])
{
	if(!IsAdmin(playerid, 1)) return SendClientMessage(playerid, COLOR_GREY, "You are unauthorized to use that command.");
	if(!IsPlayerInAnyVehicle(playerid)) return SendClientMessage(playerid, COLOR_LIGHTRED, "You are not in a vehicle.");
	new amount, msg[128];
	if(sscanf(params, "d", amount)) return SendClientMessage(playerid, COLOR_GREY, "[Usage]: /setfuel [amount]");
	if(amount < 0 || amount > 100) return SendClientMessage(playerid, COLOR_LIGHTRED, "Invalid amount! (0-100)");
	Fuel[GetPlayerVehicleID(playerid)] = amount;
	format(msg, sizeof(msg), "You have set your vehicle fuel to %d.", amount);
	SendClientMessage(playerid, COLOR_GOLD, msg);
	return 1;
}

CMD:addv(playerid, params[])
{
	if(!IsAdmin(playerid, 1)) return SendClientMessage(playerid, COLOR_GREY, "You are unauthorized to use that command.");
	if(!IsPlayerSpawned(playerid)) return SendClientMessage(playerid, COLOR_LIGHTRED, "You can't use this command now.");
	new model[32], modelid, dealerid, color1, color2, price;
	if(sscanf(params, "dsddd", dealerid, model, color1, color2, price))
		return SendClientMessage(playerid, COLOR_GREY, "[Usage]: /addv [dealerid] [model] [color1] [color2] [price]");
	if(!IsValidDealership(dealerid)) return SendClientMessage(playerid, COLOR_LIGHTRED, "Invalid dealerid!");
	if(IsNumeric(model)) modelid = strval(model);
	else modelid = GetVehicleModelIDFromName(model);
	if(modelid < 400 || modelid > 611) return SendClientMessage(playerid, COLOR_LIGHTRED, "Invalid model ID");
	if(color1 < 0 || color2 < 0) return SendClientMessage(playerid, COLOR_LIGHTRED, "Invalid color.");
	if(price < 0) return SendClientMessage(playerid, COLOR_LIGHTRED, "Invalid price.");
	new Float:X, Float:Y, Float:Z, Float:angle;
	GetPlayerPos(playerid, X, Y, Z);
	GetPlayerFacingAngle(playerid, angle);
	X += floatmul(floatsin(-angle, degrees), 4.0);
	Y += floatmul(floatcos(-angle, degrees), 4.0);
	for(new i=1; i < MAX_DVEHICLES; i++)
	{
		if(!VehicleCreated[i])
		{
			new msg[128];
			VehicleCreated[i] = VEHICLE_DEALERSHIP;
			VehicleModel[i] = modelid;
			VehiclePos[i][0] = X;
			VehiclePos[i][1] = Y;
			VehiclePos[i][2] = Z;
			VehiclePos[i][3] = angle+90.0;
			VehicleColor[i][0] = color1;
			VehicleColor[i][1] = color2;
			VehicleInterior[i] = GetPlayerInterior(playerid);
			VehicleWorld[i] = GetPlayerVirtualWorld(playerid);
			VehicleValue[i] = price;
			valstr(VehicleOwner[i], dealerid);
			VehicleNumberPlate[i] = DEFAULT_NUMBER_PLATE;
			for(new d=0; d < sizeof(VehicleTrunk[]); d++)
			{
				VehicleTrunk[i][d][0] = 0;
				VehicleTrunk[i][d][1] = 0;
			}
			for(new d=0; d < sizeof(VehicleMods[]); d++)
			{
				VehicleMods[i][d] = 0;
			}
			VehiclePaintjob[i] = 255;
			VehicleLock[i] = 0;
			VehicleAlarm[i] = 0;
			UpdateVehicle(i, 0);
			SaveVehicle(i);
			format(msg, sizeof(msg), "Added vehicle id %d to dealerid %d.", i, dealerid);
			SendClientMessage(playerid, COLOR_GOLD, msg);
			return 1;
		}
	}
	SendClientMessage(playerid, COLOR_LIGHTRED, "Can't add any more vehicles!");
	return 1;
}

CMD:editv(playerid, params[])
{
	if(!IsAdmin(playerid, 1)) return SendClientMessage(playerid, COLOR_GREY, "You are unauthorized to use that command.");
	if(GetPlayerState(playerid) == PLAYER_STATE_DRIVER)
	{
		new id = GetVehicleID(GetPlayerVehicleID(playerid));
		if(!IsValidVehicle(id)) return SendClientMessage(playerid, COLOR_LIGHTRED, "This is not a dynamic vehicle.");
		SetPVarInt(playerid, "DialogValue1", id);
		ShowDialog(playerid, DIALOG_EDITVEHICLE);
		return 1;
	}
	new vehicleid;
	if(sscanf(params, "d", vehicleid)) return SendClientMessage(playerid, COLOR_GREY, "[Usage]: /editv [vehicleid]");
	if(!IsValidVehicle(vehicleid)) return SendClientMessage(playerid, COLOR_LIGHTRED, "Invalid vehicleid.");
	SetPVarInt(playerid, "DialogValue1", vehicleid);
	ShowDialog(playerid, DIALOG_EDITVEHICLE);
	return 1;
}

CMD:adddealership(playerid, params[])
{
	if(!IsAdmin(playerid, 1)) return SendClientMessage(playerid, COLOR_GREY, "You are unauthorized to use that command.");
	if(!IsPlayerSpawned(playerid)) return SendClientMessage(playerid, COLOR_LIGHTRED, "You can't use this command now.");
	for(new i=1; i < MAX_DEALERSHIPS; i++)
	{
		if(!DealershipCreated[i])
		{
			new msg[128];
			DealershipCreated[i] = 1;
			GetPlayerPos(playerid, DealershipPos[i][0], DealershipPos[i][1], DealershipPos[i][2]);
			UpdateDealership(i, 0);
			SaveDealership(i);
			format(msg, sizeof(msg), "Added dealership id %d.", i);
			SendClientMessage(playerid, COLOR_GOLD, msg);
			return 1;
		}
	}
	SendClientMessage(playerid, COLOR_LIGHTRED, "Can't add any more dealerships.");
	return 1;
}

CMD:deletedealership(playerid, params[])
{
	if(!IsAdmin(playerid, 1)) return SendClientMessage(playerid, COLOR_GREY, "You are unauthorized to use that command.");
	new dealerid, msg[128];
	if(sscanf(params, "d", dealerid)) return SendClientMessage(playerid, COLOR_GREY, "[Usage]: /deletedealership [dealerid]");
	if(!IsValidDealership(dealerid)) return SendClientMessage(playerid, COLOR_LIGHTRED, "Invalid dealerid.");
	for(new i=1; i < MAX_DVEHICLES; i++)
	{
		if(VehicleCreated[i] == VEHICLE_DEALERSHIP && strval(VehicleOwner[i]) == dealerid)
		{
			DestroyVehicle(VehicleID[i]);
			Delete3DTextLabel(VehicleLabel[i]);
			VehicleCreated[i] = 0;
		}
	}
	DealershipCreated[dealerid] = 0;
	Delete3DTextLabel(DealershipLabel[dealerid]);
	SaveDealership(dealerid);
	format(msg, sizeof(msg), "Deleted dealership id %d.", dealerid);
	SendClientMessage(playerid, COLOR_GOLD, msg);
	return 1;
}

CMD:movedealership(playerid, params[])
{
	if(!IsAdmin(playerid, 1)) return SendClientMessage(playerid, COLOR_GREY, "You are unauthorized to use that command.");
	new dealerid, msg[128];
	if(sscanf(params, "d", dealerid)) return SendClientMessage(playerid, COLOR_GREY, "[Usage]: /movedealership [dealerid]");
	if(!IsValidDealership(dealerid)) return SendClientMessage(playerid, COLOR_LIGHTRED, "Invalid dealerid.");
	GetPlayerPos(playerid, DealershipPos[dealerid][0], DealershipPos[dealerid][1], DealershipPos[dealerid][2]);
	UpdateDealership(dealerid, 1);
	SaveDealership(dealerid);
	format(msg, sizeof(msg), "Moved dealership id %d here.", dealerid);
	SendClientMessage(playerid, COLOR_GOLD, msg);
	return 1;
}

CMD:gotodealership(playerid, params[])
{
	if(!IsAdmin(playerid, 1)) return SendClientMessage(playerid, COLOR_GREY, "You are unauthorized to use that command.");
	new dealerid, msg[128];
	if(sscanf(params, "d", dealerid)) return SendClientMessage(playerid, COLOR_GREY, "[Usage]: /gotodealership [dealerid]");
	if(!IsValidDealership(dealerid)) return SendClientMessage(playerid, COLOR_LIGHTRED, "Invalid dealerid");
	SetPlayerPos(playerid, DealershipPos[dealerid][0], DealershipPos[dealerid][1], DealershipPos[dealerid][2]);
	format(msg, sizeof(msg), "Teleported to dealership id %d.", dealerid);
	SendClientMessage(playerid, COLOR_GOLD, msg);
	return 1;
}

CMD:addfuelstation(playerid, params[])
{
	if(!IsAdmin(playerid, 1)) return SendClientMessage(playerid, COLOR_GREY, "You are unauthorized to use that command.");
	if(!IsPlayerSpawned(playerid)) return SendClientMessage(playerid, COLOR_LIGHTRED, "You can't use this command now.");
	for(new i=1; i < MAX_FUEL_STATIONS; i++)
	{
		if(!FuelStationCreated[i])
		{
			new msg[128];
			FuelStationCreated[i] = 1;
			GetPlayerPos(playerid, FuelStationPos[i][0], FuelStationPos[i][1], FuelStationPos[i][2]);
			UpdateFuelStation(i, 0);
			SaveFuelStation(i);
			format(msg, sizeof(msg), "Added fuel station id %d.", i);
			SendClientMessage(playerid, COLOR_GOLD, msg);
			return 1;
		}
	}
	SendClientMessage(playerid, COLOR_LIGHTRED, "Can't add any more fuel stations.");
	return 1;
}

CMD:deletefuelstation(playerid, params[])
{
	if(!IsAdmin(playerid, 1)) return SendClientMessage(playerid, COLOR_GREY, "You are unauthorized to use that command.");
	new stationid, msg[128];
	if(sscanf(params, "d", stationid)) return SendClientMessage(playerid, COLOR_GREY, "[Usage]: /deletefuelstation [stationid]");
	if(!IsValidFuelStation(stationid)) return SendClientMessage(playerid, COLOR_LIGHTRED, "Invalid stationid.");
	FuelStationCreated[stationid] = 0;
	Delete3DTextLabel(FuelStationLabel[stationid]);
	SaveFuelStation(stationid);
	format(msg, sizeof(msg), "Deleted fuel station id %d.", stationid);
	SendClientMessage(playerid, COLOR_GOLD, msg);
	return 1;
}

CMD:movefuelstation(playerid, params[])
{
	if(!IsAdmin(playerid, 1)) return SendClientMessage(playerid, COLOR_GREY, "You are unauthorized to use that command.");
	new stationid, msg[128];
	if(sscanf(params, "d", stationid)) return SendClientMessage(playerid, COLOR_GREY, "[Usage]: /movefuelstation [stationid]");
	if(!IsValidFuelStation(stationid)) return SendClientMessage(playerid, COLOR_LIGHTRED, "Invalid stationid.");
	GetPlayerPos(playerid, FuelStationPos[stationid][0], FuelStationPos[stationid][1], FuelStationPos[stationid][2]);
	UpdateFuelStation(stationid, 1);
	SaveFuelStation(stationid);
	format(msg, sizeof(msg), "Moved fuel station id %d here.", stationid);
	SendClientMessage(playerid, COLOR_GOLD, msg);
	return 1;
}

CMD:gotofuelstation(playerid, params[])
{
	if(!IsAdmin(playerid, 1)) return SendClientMessage(playerid, COLOR_GREY, "You are unauthorized to use that command.");
	new stationid, msg[128];
	if(sscanf(params, "d", stationid)) return SendClientMessage(playerid, COLOR_GREY, "USAGE: /gotofuelstation [stationid]");
	if(!IsValidFuelStation(stationid)) return SendClientMessage(playerid, COLOR_LIGHTRED, "Invalid stationid.");
	SetPlayerPos(playerid, FuelStationPos[stationid][0], FuelStationPos[stationid][1], FuelStationPos[stationid][2]);
	format(msg, sizeof(msg), "Teleported to fuel station id %d.", stationid);
	SendClientMessage(playerid, COLOR_GOLD, msg);
	return 1;
}

/*

	[=General Commands=]
	
*/

CMD:greet(playerid, params[])
{
    new id, number, string[64], Float:X, Float:Y, Float:Z;
    GetPlayerPos(id, X, Y, Z);

    if(sscanf(params,"u", id, number)) return SCM(playerid, COLOR_GREY,"[Usage]: /greet [playerid/partofname] [greet (0-6)].");
    if(playerid == id) return SCM(playerid, COLOR_LIGHTRED,"[Error]: You can't greet yourself.");

    if(IsPlayerInRangeOfPoint(playerid, 7.0, X, Y, Z))
	{
 		format(string, sizeof(string), "* %s would like to greet you, /acceptgreet.", GetName(playerid));
    	SendClientMessage(playerid, COLOR_GOLD, string);
		greetInvited[id] = true;
		greetNumber[id] = number;
  		Player_Greet[id] = playerid;
	} else return SCM(playerid, COLOR_LIGHTRED, "[Error]: You're not close enough.");
  	return 1;
}

CMD:acceptgreet(playerid, params[])
{
    if(greetInvited[playerid] == false) return SCM(playerid, COLOR_LIGHTRED,"[Error]: You're not invited to greet anyone");
    if(greetNumber[playerid] == 1)
    {
    	ApplyAnimation(playerid, "GANGS", "hndshkfa", 4.1, 0, 1, 1, 1, 1, 1);
	    ApplyAnimation(Player_Greet[playerid], "GANGS", "hndshkfa", 4.1, 0, 1, 1, 1, 1, 1);
	}
	else if(greetNumber[playerid] == 2)
	{
	    ApplyAnimation(playerid, "GANGS", "hndshkaa", 4.1, 0, 1, 1, 1, 1, 1);
     	ApplyAnimation(Player_Greet[playerid], "GANGS", "hndshkaa", 4.1, 0, 1, 1, 1, 1, 1);
	}
	else if(greetNumber[playerid] == 3)
	{
	    ApplyAnimation(playerid, "GANGS", "hndshkba", 4.1, 0, 1, 1, 1, 1, 1);
     	ApplyAnimation(Player_Greet[playerid], "GANGS", "hndshkba", 4.1, 0, 1, 1, 1, 1, 1);
	}
	else if(greetNumber[playerid] == 4)
	{
	    ApplyAnimation(playerid, "GANGS", "hndshkca", 4.1, 0, 1, 1, 1, 1, 1);
     	ApplyAnimation(Player_Greet[playerid], "GANGS", "hndshkca", 4.1, 0, 1, 1, 1, 1, 1);
	}
	else if(greetNumber[playerid] == 5)
	{
	    ApplyAnimation(playerid, "GANGS", "hndshkda", 4.1, 0, 1, 1, 1, 1, 1);
     	ApplyAnimation(Player_Greet[playerid], "GANGS", "hndshkda", 4.1, 0, 1, 1, 1, 1, 1);
	}
	else if(greetNumber[playerid] == 6)
	{
	    ApplyAnimation(playerid, "GANGS", "hndshkea", 4.1, 0, 1, 1, 1, 1, 1);
		ApplyAnimation(Player_Greet[playerid], "GANGS", "hndshkea", 4.1, 0, 1, 1, 1, 1, 1);
	}
	return 1;
}

CMD:givegun(playerid, params[])
{
    new id, string[124], Float:X, Float:Y, Float:Z, playergun, playerammo;
    playergun = GetPlayerWeapon(playerid);
    playerammo = GetPlayerAmmo(playerid);

    if(sscanf(params,"u", id)) return SCM(playerid, COLOR_GREY,"[Usage]: /givegun [playerid/partofname].");
    if(playergun < 1) return SCM(playerid, COLOR_LIGHTRED,"[Error]: You do not have a weapon.");
    if(playerammo < 1) return SCM(playerid, COLOR_LIGHTRED,"[Error]: You do not have any ammo.");
    if(playerid == id) return SCM(playerid, COLOR_LIGHTRED,"[Error]: You can't give a weapon to yourself.");

    GetPlayerPos(id, X, Y, Z);
    if(IsPlayerInRangeOfPoint(playerid, 7.0, X, Y, Z))
	{
		GivePlayerWeapon(id, playergun, playerammo);
		GivePlayerWeapon(playerid, playergun, -playerammo);

	    format(string, sizeof(string), "%s hands a weapon to %s.", GetName(playerid), GetName(id));
	   	ProxDetector(10.0, playerid, string, COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE);
	} else return SCM(playerid, COLOR_LIGHTRED, "[Error]: You're not close enough.");
  	return 1;
}

CMD:dice(playerid, params[])
{
	new
	dice = 0 + random(6), string[64];
	if(Dice[playerid] == 0) SCM(playerid, COLOR_LIGHTRED, "* You do not have a dice.");
 	format(string, sizeof(string), "%s rolls a dice that lands on %d.", GetName(playerid), dice);
	ProxDetector(10.0, playerid, string, COLOR_WHITE,COLOR_WHITE,COLOR_WHITE,COLOR_WHITE,COLOR_WHITE);
  	return 1;
}

CMD:animlist(playerid, params[])
{
	SCM(playerid, COLOR_GREEN, "_______________________________"COL_WHITE"[ANIMATIONS]"COL_GREEN"_______________________________");
	SCM(playerid, -1, "[ANIMS:] /crack [1-2] /chat /caract /hike /give /pull /face /endchat /show /shoutanim /look /drunk /sit [1-4]");
	SCM(playerid, -1, "[ANIMS:] /scratch /reload /injured /dive /sign [1-4] /chill [1-3] /gwalk [1-2] /grafitti [1-2] /camera [1-3]");
	SCM(playerid, -1, "[ANIMS:] /rap /think /box /tired /cop /stance [1-2] /bar [1-2] /bat [1-3] /lean /dance [1-7] /kiss /cpr /vomit");
	SCM(playerid, -1, "[ANIMS:] /handsup /bomb /getarrested /laugh /lookout /aim /crossarms /car [1-3] /lay [1-3] /what [1-2] /hide");
	SCM(playerid, -1, "[ANIMS:] /eat /wave /chant /slap /deal /fuck /taichi");
  	return 1;
}

CMD:frisk(playerid, params[])
{
	new Player_Weapons[13];
	new Player_Ammos[13];
	new string[256];
	new i, id;
	
    if(sscanf(params,"u", id)) return SCM(playerid, COLOR_GREY,"[Usage]: /frisk [playerid/partofname].");
   	format(string, sizeof(string),"__________"COL_WHITE"[%s]"COL_GREEN"__________", GetName(id));
	SCM(playerid, COLOR_GREEN, string);
	for(i = 1;i <= 12;i++)
	{
		GetPlayerWeaponData(id,i,Player_Weapons[i],Player_Ammos[i]);
		if(Player_Weapons[i] != 0)
		{
			new weaponName[128];
			GetWeaponName(Player_Weapons[i],weaponName,128);
			format(string,255,"Weapon Name: %s | Weapon Ammo: %d",weaponName,Player_Ammos[i]);
			SendClientMessage(playerid,-1,string);
		}
	}
	return 1;
}


CMD:revokeguns(playerid, params[])
{
	new id;
	
	if(Duty[playerid] == 0) return SCM(playerid, COLOR_LIGHTRED, "* You're not on duty.");
    if(sscanf(params,"u", id)) return SCM(playerid, COLOR_GREY,"[Usage]: /revokeguns [playerid/partofname].");
    RemoveWeapons(id);
	return 1;
}

CMD:revokedrugs(playerid, params[])
{
	new id;

	if(Duty[playerid] == 0) return SCM(playerid, COLOR_LIGHTRED, "* You're not on duty.");
    if(sscanf(params,"u", id)) return SCM(playerid, COLOR_GREY,"[Usage]: /revokedrugs [playerid/partofname].");
    RemoveDrugs(id);
	return 1;
}

CMD:rentcar(playerid, params[])
{
    if(GetPlayerState(playerid) == 2)
    {
		if(GetPlayerCash(playerid) < 9) return SCM(playerid, COLOR_LIGHTRED, "* You do not have enough money.");
		SCM(playerid, COLOR_GOLD, "* You have rented this vehicle for $10. Type /engine to start it.");
		rentingVehicle[playerid] = true;
		GivePlayerCash(playerid, -10);
		TogglePlayerControllable(playerid,1);
	}
	return 1;
}

CMD:buy(playerid, params[])
{
    if(IsPlayerInRangeOfPoint(playerid, 7.0, -23.5424,-55.6289,1003.5469) || IsPlayerInRangeOfPoint(playerid, 7.0, -31.0680,-29.0295,1003.5573) || IsPlayerInRangeOfPoint(playerid, 7.0, -22.2473,-138.6266,1003.5469) || IsPlayerInRangeOfPoint(playerid, 7.0, -28.2207,-89.9549,1003.5469))
	{
 		ShowPlayerDialog(playerid, DIALOG_BUY, DIALOG_STYLE_LIST, "24/7", "6 Pack of Beers ($15)\nPack of Cigarettes ($5)\nDice ($1)\nMask ($50)\nWater Bottle ($10)", "Purchase", "Cancel");
	} else return SCM(playerid, COLOR_LIGHTRED, "[Error]: You are not inside a 24/7.");
  	return 1;
}

CMD:buyboombox(playerid, params[])
{
    if(IsPlayerInRangeOfPoint(playerid, 7.0, -2237.1465,130.1773,1035.4141))
	{
	    if(GetPlayerCash(playerid) < 1000) return SCM(playerid, COLOR_LIGHTRED, "* You don't have enough money.");
		PlayerInfo[playerid][pBoombox] = 1;
	} else return SCM(playerid, COLOR_LIGHTRED, "[Error]: You are not inside a electronic store.");
  	return 1;
}

CMD:train(playerid, params[])
{
    if(IsPlayerInRangeOfPoint(playerid, 7.0, 772.2167,5.2337,1000.7802) || IsPlayerInRangeOfPoint(playerid, 7.0, 759.2585,-59.2561,1000.7802))
	{
 		ShowPlayerDialog(playerid, DIALOG_TRAIN, DIALOG_STYLE_LIST, "Gym", "Normal ($10)\nBoxing ($20)\nKneehead($20)\nKung-Fu ($20)", "Learn", "Cancel");
	} else return SCM(playerid, COLOR_LIGHTRED, "[Error]: You are not inside a gym.");
  	return 1;
}

CMD:lockbiz(playerid, params[])
{
    new id = IsPlayerNearBizEnt(playerid);
    if(id != PlayerInfo[playerid][BizID]) return SCM(playerid, COLOR_LIGHTRED, "[Error]: You do not own this business.");
    if(BusinessInfo[id][bLocked] == 1)
    {
        BusinessInfo[id][bLocked] = 0;
        GameTextForPlayer(playerid, "~w~business ~g~ UNLOCKED", 3000, 6);
        PlayerPlaySound(playerid, 1145, 0.0, 0.0, 0.0);
        
       	new file4[40];
		format(file4, sizeof(file4), BPATH, id);
		new INI:File = INI_Open(file4);
		INI_SetTag(File,"data");
		INI_WriteInt(File,"bLocked", BusinessInfo[id][bLocked]);
		INI_Close(File);
    }
    else
    {
        BusinessInfo[id][bLocked] = 1;
        GameTextForPlayer(playerid, "~w~business ~r~ LOCKED", 3000, 6);
        PlayerPlaySound(playerid, 1145, 0.0, 0.0, 0.0);
        
       	new file4[40];
		format(file4, sizeof(file4), BPATH, id);
		new INI:File = INI_Open(file4);
		INI_SetTag(File,"data");
		INI_WriteInt(File,"bLocked", BusinessInfo[id][bLocked]);
		INI_Close(File);
    }
    return 1;
}

CMD:alockbiz(playerid, params[])
{
    new id = IsPlayerNearBizEnt(playerid);
    if(PlayerInfo[playerid][pAdmin] < 3) return SCM(playerid, COLOR_GREY,"[Error]: You're not authorized to use this command.");
    if(BusinessInfo[id][bLocked] == 1)
    {
        BusinessInfo[id][bLocked] = 0;
        GameTextForPlayer(playerid, "~w~business ~g~ UNLOCKED", 3000, 6);
        PlayerPlaySound(playerid, 1145, 0.0, 0.0, 0.0);
        
       	new file4[40];
		format(file4, sizeof(file4), BPATH, id);
		new INI:File = INI_Open(file4);
		INI_SetTag(File,"data");
		INI_WriteInt(File,"bLocked", BusinessInfo[id][bLocked]);
		INI_Close(File);
    }
    else if(BusinessInfo[id][bLocked] == 0)
    {
        BusinessInfo[id][bLocked] = 1;
        GameTextForPlayer(playerid, "~w~business ~r~ LOCKED", 3000, 6);
        PlayerPlaySound(playerid, 1145, 0.0, 0.0, 0.0);
        
       	new file4[40];
		format(file4, sizeof(file4), BPATH, id);
		new INI:File = INI_Open(file4);
		INI_SetTag(File,"data");
		INI_WriteInt(File,"bLocked", BusinessInfo[id][bLocked]);
		INI_Close(File);
    }
    else return SCM(playerid, COLOR_LIGHTRED, "[Error]: You're not close to any business.");
    return 1;
}

CMD:agotobiz(playerid, params[])
{
    new id, str[64];

    if(sscanf(params, "d", id)) return SendClientMessage(playerid, COLOR_GREY, "[Usage]: /agotobusiness [id] (street number is the ID)");
    
    SetPlayerPos(playerid, BusinessInfo[id][bEntranceX], BusinessInfo[id][bEntranceY], BusinessInfo[id][bEntranceZ]);
    format(str, sizeof(str), "AdmCmd: You have succesfully teleported to business id %d.", id);
	SCM(playerid, COLOR_LIGHTRED, str);
    return 1;
}

CMD:abizname(playerid, params[])
{
    new
	name[128], biztext[24];
	new string[128];

 	new
	id = IsPlayerNearBizEnt(playerid);

    if(sscanf(params, "s[128]", name)) return SCM(playerid, COLOR_GREY, "[Usage]: /abizname [name]");
    SCM(playerid, COLOR_LIGHTRED, "AdmCmd: You have succesfully changed the name of this business.");
   	switch(BusinessInfo[id][bType])
    {
 			case 20: biztext = "Dealership";
 			case 19: biztext = "Electronic Store";
   			case 18: biztext = "Ammunition";
   			case 17: biztext = "Gym";
   			case 16: biztext = "Hotel";
   			case 15: biztext = "Motel";
   			case 14: biztext = "Diner";
         	case 13: biztext = "Tattoo Store";
         	case 12: biztext = "Barbershop";
            case 11: biztext = "Flower Store";
           	case 10: biztext = "98 Cents";
    		case 9: biztext = "69 Cents";
            case 8: biztext = "Liqour Store";
	    	case 7: biztext = "Restaurant";
	    	case 6: biztext = "Bank";
	    	case 5: biztext = "Hospital";
	        case 4: biztext = "Police Station";
	        case 3: biztext = "24/7";
	        case 2: biztext = "Club";
	        case 1: biztext = "Bar";
	        case 0: biztext = "Clothes Shop";
    }
 	BusinessInfo[id][bName] = name;
    format(string,sizeof(string),""COL_BROWN"Owner: "COL_WHITE"%s\n"COL_BROWN"Name: "COL_WHITE"%s\n"COL_BROWN"Type: "COL_WHITE"%s\n"COL_BROWN"Street Number: "COL_WHITE"%d", BusinessInfo[id][bPrice], BusinessInfo[id][bName], biztext, id);
	Update3DTextLabelText(BusinessInfo[id][DLabel], 0xFFFFFFFF, string);
	new file4[40];
	format(file4, sizeof(file4), BPATH, id);
	new INI:File = INI_Open(file4);
	INI_SetTag(File,"data");
	INI_WriteString(File,"bName", BusinessInfo[id][bName]);
	INI_Close(File);
    return 1;
}


CMD:enter(playerid, params[])
{
    for(new b = 1; b < sizeof(BusinessInfo); b++)
    {
        if(IsPlayerInRangeOfPoint(playerid, 2.0, BusinessInfo[b][bEntranceX], BusinessInfo[b][bEntranceY], BusinessInfo[b][bEntranceZ]))
        {
            if(BusinessInfo[b][bLocked] == 1) return SendClientMessage(playerid, COLOR_GOLD, "* This business is locked.");
            SetPlayerPos(playerid, BusinessInfo[b][bExitX], BusinessInfo[b][bExitY], BusinessInfo[b][bExitZ]);
            SetPlayerFacingAngle(playerid, BusinessInfo[b][bExitA]);
            SetPlayerInterior(playerid, BusinessInfo[b][bInsideInt]);
            SetPlayerVirtualWorld(playerid, BusinessInfo[b][bInsideWorld]);
            InsideBiz[playerid] = b;
            TogglePlayerControllable(playerid,0);
            SetTimerEx("LoadInterior", 3000, false, "i", playerid);
            return 1;
        }
    }
    for(new h = 1; h < sizeof(HouseInfo); h++)
    {
        if(IsPlayerInRangeOfPoint(playerid, 2.0, HouseInfo[h][hEntranceX], HouseInfo[h][hEntranceY], HouseInfo[h][hEntranceZ]))
        {
            if(HouseInfo[h][hLocked] == 1) return SendClientMessage(playerid, COLOR_GOLD, "* This house is locked.");
            SetPlayerPos(playerid, HouseInfo[h][hExitX], HouseInfo[h][hExitY], HouseInfo[h][hExitZ]);
            SetPlayerFacingAngle(playerid, HouseInfo[h][hExitA]);
            SetPlayerInterior(playerid, HouseInfo[h][hInsideInt]);
            SetPlayerVirtualWorld(playerid, HouseInfo[h][hInsideWorld]);
            InsideHouse[playerid] = h;
            TogglePlayerControllable(playerid,0);
            SetTimerEx("LoadInterior", 3000, false, "i", playerid);
            return 1;
        }
    }
    return 1;
}

CMD:exit(playerid, params[])
{
    for(new b = 1; b < sizeof(BusinessInfo); b++)//Loops through all the businesses.
    {
        if(IsPlayerInRangeOfPoint(playerid, 5.0, BusinessInfo[b][bExitX], BusinessInfo[b][bExitY], BusinessInfo[b][bExitZ]) && GetPlayerVirtualWorld(playerid) == BusinessInfo[b][bInsideWorld])//Checks if player is in near the exit.
        {
            SetPlayerPos(playerid, BusinessInfo[b][bEntranceX], BusinessInfo[b][bEntranceY], BusinessInfo[b][bEntranceZ]);
            SetPlayerFacingAngle(playerid, BusinessInfo[b][bEntranceA]);
            SetPlayerInterior(playerid, BusinessInfo[b][bInt]);
            SetPlayerVirtualWorld(playerid, BusinessInfo[b][bWorld]);
            InsideBiz[playerid] = 0;
            return 1;
        }
    }
    for(new h = 1; h < sizeof(HouseInfo); h++)
    {
        if(IsPlayerInRangeOfPoint(playerid, 5.0, HouseInfo[h][hExitX], HouseInfo[h][hExitY], HouseInfo[h][hExitZ]) && GetPlayerVirtualWorld(playerid) == HouseInfo[h][hInsideWorld])
        {
            SetPlayerPos(playerid, HouseInfo[h][hEntranceX], HouseInfo[h][hEntranceY], HouseInfo[h][hEntranceZ]);
            SetPlayerFacingAngle(playerid, HouseInfo[h][hEntranceA]);
            SetPlayerInterior(playerid, HouseInfo[h][hInt]);
            SetPlayerVirtualWorld(playerid, HouseInfo[h][hWorld]);
            InsideHouse[playerid] = h;
            TogglePlayerControllable(playerid,0);
            SetTimerEx("LoadInterior", 3000, false, "i", playerid);
            return 1;
        }
    }
    return 1;
}

CMD:sellbiz(playerid, params[])
{
    new
	id2 = PlayerInfo[playerid][BizID];
	
	new biztext[24];
	new string[128];
	
    if(PlayerInfo[playerid][BizID] == 0) return SCM(playerid, COLOR_LIGHTRED, "[Error]: You do not own a business.");
    BusinessInfo[id2][bOwned] = 0;
    BusinessInfo[id2][bOwner] = 0;
    BusinessInfo[id2][bLocked] = 1;
    BusinessInfo[id2][bName] = 0;
    GivePlayerCash(playerid, BusinessInfo[id2][bPrice]);
    PlayerInfo[playerid][BizID] = 0;
    SCM(playerid, COLOR_GOLD, "* You have succesfully sold your business. Sad to see it go.");
    
   	switch(BusinessInfo[id2][bType])
    {
 			case 20: biztext = "Dealership";
 			case 19: biztext = "Electronic Store";
   			case 18: biztext = "Ammunition";
   			case 17: biztext = "Gym";
   			case 16: biztext = "Hotel";
   			case 15: biztext = "Motel";
   			case 14: biztext = "Diner";
         	case 13: biztext = "Tattoo Store";
         	case 12: biztext = "Barbershop";
            case 11: biztext = "Flower Store";
           	case 10: biztext = "98 Cents";
    		case 9: biztext = "69 Cents";
            case 8: biztext = "Liqour Store";
	    	case 7: biztext = "Restaurant";
	    	case 6: biztext = "Bank";
	    	case 5: biztext = "Hospital";
	        case 4: biztext = "Police Station";
	        case 3: biztext = "24/7";
	        case 2: biztext = "Club";
	        case 1: biztext = "Bar";
	        case 0: biztext = "Clothes Shop";
    }
    
   	format(string,sizeof(string),""COL_BROWN"Owner: "COL_WHITE"None\n"COL_BROWN"Price: "COL_WHITE"$%d\n"COL_BROWN"Type: "COL_WHITE"%s\n"COL_BROWN"Street Number: "COL_WHITE"%d", BusinessInfo[id2][bName], BusinessInfo[id2][bPrice], biztext, id2);
	Update3DTextLabelText(BusinessInfo[id2][DLabel], 0xFFFFFFFF, string);
	new file4[40];
	format(file4, sizeof(file4), BPATH, id2);
	new INI:File = INI_Open(file4);
	INI_SetTag(File,"data");
	INI_WriteInt(File,"bOwned", BusinessInfo[id2][bOwned]);
	INI_WriteInt(File,"bPrice", BusinessInfo[id2][bPrice]);
	INI_WriteString(File,"bOwner", BusinessInfo[id2][bOwner]);
	INI_WriteInt(File,"bType", BusinessInfo[id2][bType]);
	INI_WriteInt(File,"bLocked", BusinessInfo[id2][bLocked]);
	INI_WriteInt(File,"bMoney", BusinessInfo[id2][bMoney]);
	INI_WriteFloat(File,"bEntranceX", BusinessInfo[id2][bEntranceX]);
	INI_WriteFloat(File,"bEntranceY", BusinessInfo[id2][bEntranceY]);
	INI_WriteFloat(File,"bEntranceZ", BusinessInfo[id2][bEntranceZ]);
	INI_WriteFloat(File,"bEntranceA", BusinessInfo[id2][bEntranceA]);
	INI_WriteFloat(File,"bExitX", BusinessInfo[id2][bExitX]);
	INI_WriteFloat(File,"bExitY", BusinessInfo[id2][bExitY]);
	INI_WriteFloat(File,"bExitZ", BusinessInfo[id2][bExitZ]);
	INI_WriteFloat(File,"bExitA", BusinessInfo[id2][bExitA]);
	INI_WriteInt(File,"bInt", BusinessInfo[id2][bInt]);
	INI_WriteInt(File,"bWorld", BusinessInfo[id2][bWorld]);
	INI_WriteInt(File,"bInsideInt", BusinessInfo[id2][bInsideInt]);
	INI_WriteInt(File,"bInsideWorld", BusinessInfo[id2][bInsideWorld]);
	INI_WriteString(File,"bName", BusinessInfo[id2][bName]);
	INI_Close(File);
    return 1;
}

CMD:asellbiz(playerid, params[])
{
    new id = IsPlayerNearBizEnt(playerid);
   	new biztext[24];
	new string[144];
    if(PlayerInfo[playerid][pAdmin] < 3) return SCM(playerid, COLOR_GREY,"[Error]: You're not authorized to use this command.");
    if(BusinessInfo[id][bOwned] == 0) return SCM(playerid, COLOR_LIGHTRED,"[Error]: This business is not owned by anyone.");
    BusinessInfo[id][bOwned] = 0;
    BusinessInfo[id][bOwner] = 0;
    BusinessInfo[id][bName] = 0;
    BusinessInfo[id][bLocked] = 1;
    SCM(playerid, COLOR_LIGHTRED, "AdmCmd: You have succesfully admin-sold this business.");
    
   	switch(BusinessInfo[id][bType])
    {
 			case 20: biztext = "Dealership";
 			case 19: biztext = "Electronic Store";
   			case 18: biztext = "Ammunition";
   			case 17: biztext = "Gym";
   			case 16: biztext = "Hotel";
   			case 15: biztext = "Motel";
   			case 14: biztext = "Diner";
         	case 13: biztext = "Tattoo Store";
         	case 12: biztext = "Barbershop";
            case 11: biztext = "Flower Store";
           	case 10: biztext = "98 Cents";
    		case 9: biztext = "69 Cents";
            case 8: biztext = "Liqour Store";
	    	case 7: biztext = "Restaurant";
	    	case 6: biztext = "Bank";
	    	case 5: biztext = "Hospital";
	        case 4: biztext = "Police Station";
	        case 3: biztext = "24/7";
	        case 2: biztext = "Club";
	        case 1: biztext = "Bar";
	        case 0: biztext = "Clothes Shop";
    }
	
 	format(string,sizeof(string),""COL_BROWN"Owner: "COL_WHITE"None\n"COL_BROWN"Price: "COL_WHITE"$%d\n"COL_BROWN"Type: "COL_WHITE"%s\n"COL_BROWN"Street Number: "COL_WHITE"%d", BusinessInfo[id][bName], BusinessInfo[id][bPrice], biztext, id);
	Update3DTextLabelText(BusinessInfo[id][DLabel], 0xFFFFFFFF, string);
    
	new file4[40];
	format(file4, sizeof(file4), BPATH, id);
	new INI:File = INI_Open(file4);
	INI_SetTag(File,"data");
	INI_WriteInt(File,"bOwned", BusinessInfo[id][bOwned]);
	INI_WriteInt(File,"bPrice", BusinessInfo[id][bPrice]);
	INI_WriteString(File,"bOwner", BusinessInfo[id][bOwner]);
	INI_WriteInt(File,"bType", BusinessInfo[id][bType]);
	INI_WriteInt(File,"bLocked", BusinessInfo[id][bLocked]);
	INI_WriteInt(File,"bMoney", BusinessInfo[id][bMoney]);
	INI_WriteFloat(File,"bEntranceX", BusinessInfo[id][bEntranceX]);
	INI_WriteFloat(File,"bEntranceY", BusinessInfo[id][bEntranceY]);
	INI_WriteFloat(File,"bEntranceZ", BusinessInfo[id][bEntranceZ]);
	INI_WriteFloat(File,"bEntranceA", BusinessInfo[id][bEntranceA]);
	INI_WriteFloat(File,"bExitX", BusinessInfo[id][bExitX]);
	INI_WriteFloat(File,"bExitY", BusinessInfo[id][bExitY]);
	INI_WriteFloat(File,"bExitZ", BusinessInfo[id][bExitZ]);
	INI_WriteFloat(File,"bExitA", BusinessInfo[id][bExitA]);
	INI_WriteInt(File,"bInt", BusinessInfo[id][bInt]);
	INI_WriteInt(File,"bWorld", BusinessInfo[id][bWorld]);
	INI_WriteInt(File,"bInsideInt", BusinessInfo[id][bInsideInt]);
	INI_WriteInt(File,"bInsideWorld", BusinessInfo[id][bInsideWorld]);
	INI_WriteString(File,"bName", BusinessInfo[id][bName]);
	INI_Close(File);
    return 1;
}

CMD:bizname(playerid, params[])
{
    new
	name[128], biztext[24];
	new string[128];
	
 	new
	id = IsPlayerNearBizEnt(playerid);
	
 	if(id != PlayerInfo[playerid][BizID]) return SCM(playerid, COLOR_LIGHTRED, "[Error]: You do not own this business.");
    if(sscanf(params, "s[128]", name)) return SCM(playerid, COLOR_GREY, "[Usage]: /bizname [name]");
    if(PlayerInfo[playerid][BizID] == 0) return SCM(playerid, COLOR_GREY, "[Error]: You do not own a business!");
    BusinessInfo[PlayerInfo[playerid][BizID]][bName] = name;
    SCM(playerid, COLOR_GOLD, "* You have succesfully changed the name of your business.");
    
   	switch(BusinessInfo[id][bType])
    {
 			case 20: biztext = "Dealership";
 			case 19: biztext = "Electronic Store";
   			case 18: biztext = "Ammunition";
   			case 17: biztext = "Gym";
   			case 16: biztext = "Hotel";
   			case 15: biztext = "Motel";
   			case 14: biztext = "Diner";
         	case 13: biztext = "Tattoo Store";
         	case 12: biztext = "Barbershop";
            case 11: biztext = "Flower Store";
           	case 10: biztext = "98 Cents";
    		case 9: biztext = "69 Cents";
            case 8: biztext = "Liqour Store";
	    	case 7: biztext = "Restaurant";
	    	case 6: biztext = "Bank";
	    	case 5: biztext = "Hospital";
	        case 4: biztext = "Police Station";
	        case 3: biztext = "24/7";
	        case 2: biztext = "Club";
	        case 1: biztext = "Bar";
	        case 0: biztext = "Clothes Shop";
    }

    format(string,sizeof(string),""COL_BROWN"Owner: "COL_WHITE"%s\n"COL_BROWN"Name: "COL_WHITE"%s\n"COL_BROWN"Type: "COL_WHITE"%s\n"COL_BROWN"Street Number: "COL_WHITE"%d", BusinessInfo[id][bOwner], BusinessInfo[id][bName], biztext, id);
	Update3DTextLabelText(BusinessInfo[id][DLabel], 0xFFFFFFFF, string);
	new file4[40];
	format(file4, sizeof(file4), BPATH, id);
	new INI:File = INI_Open(file4);
	INI_SetTag(File,"data");
	INI_WriteInt(File,"bOwned", BusinessInfo[id][bOwned]);
	INI_WriteInt(File,"bPrice", BusinessInfo[id][bPrice]);
	INI_WriteString(File,"bOwner", BusinessInfo[id][bOwner]);
	INI_WriteInt(File,"bType", BusinessInfo[id][bType]);
	INI_WriteInt(File,"bLocked", BusinessInfo[id][bLocked]);
	INI_WriteInt(File,"bMoney", BusinessInfo[id][bMoney]);
	INI_WriteFloat(File,"bEntranceX", BusinessInfo[id][bEntranceX]);
	INI_WriteFloat(File,"bEntranceY", BusinessInfo[id][bEntranceY]);
	INI_WriteFloat(File,"bEntranceZ", BusinessInfo[id][bEntranceZ]);
	INI_WriteFloat(File,"bEntranceA", BusinessInfo[id][bEntranceA]);
	INI_WriteFloat(File,"bExitX", BusinessInfo[id][bExitX]);
	INI_WriteFloat(File,"bExitY", BusinessInfo[id][bExitY]);
	INI_WriteFloat(File,"bExitZ", BusinessInfo[id][bExitZ]);
	INI_WriteFloat(File,"bExitA", BusinessInfo[id][bExitA]);
	INI_WriteInt(File,"bInt", BusinessInfo[id][bInt]);
	INI_WriteInt(File,"bWorld", BusinessInfo[id][bWorld]);
	INI_WriteInt(File,"bInsideInt", BusinessInfo[id][bInsideInt]);
	INI_WriteInt(File,"bInsideWorld", BusinessInfo[id][bInsideWorld]);
	INI_WriteString(File,"bName", BusinessInfo[id][bName]);
	INI_Close(File);
    return 1;
}

CMD:alockhouse(playerid, params[])
{
    new id = IsPlayerNearHouseEnt(playerid);
    if(PlayerInfo[playerid][pAdmin] < 3) return SCM(playerid, COLOR_GREY,"[Error]: You're not authorized to use this command.");
    if(HouseInfo[id][hLocked] == 1)
    {
        HouseInfo[id][hLocked] = 0;
        GameTextForPlayer(playerid, "~w~house ~g~ UNLOCKED", 3000, 6);
        PlayerPlaySound(playerid, 1145, 0.0, 0.0, 0.0);

       	new file4[40];
		format(file4, sizeof(file4), HPATH, id);
		new INI:File = INI_Open(file4);
		INI_SetTag(File,"data");
		INI_WriteInt(File,"hLocked", HouseInfo[id][hLocked]);
		INI_Close(File);
    }
    else if(HouseInfo[id][hLocked] == 0)
    {
        HouseInfo[id][hLocked] = 1;
        GameTextForPlayer(playerid, "~w~house ~r~ LOCKED", 3000, 6);
        PlayerPlaySound(playerid, 1145, 0.0, 0.0, 0.0);

       	new file4[40];
		format(file4, sizeof(file4), HPATH, id);
		new INI:File = INI_Open(file4);
		INI_SetTag(File,"data");
		INI_WriteInt(File,"hLocked", HouseInfo[id][hLocked]);
		INI_Close(File);
    }
    else return SCM(playerid, COLOR_LIGHTRED, "[Error]: You're not close to any house.");
    return 1;
}

CMD:lockhouse(playerid, params[])
{
    new id = IsPlayerNearHouseEnt(playerid);
    new id2 = IsPlayerInsideHouse(playerid);
   	new hworld = GetPlayerVirtualWorld(playerid);
   	
    if(!GetPlayerInterior(playerid)) // He is outside any house ( interior = 0)
    {
        if(id != PlayerInfo[playerid][HouseID]) return SCM(playerid, COLOR_LIGHTRED, "[Error]: You do not own this house.");
    }
    else // He isn't outside
    {
        if(id2 != PlayerInfo[playerid][HouseID]) return SCM(playerid, COLOR_LIGHTRED, "[Error]: You do not own this house.");
    }
    if(HouseInfo[id][hLocked] == 1)
    {
        HouseInfo[id][hLocked] = 0;
        GameTextForPlayer(playerid, "~w~house ~g~ UNLOCKED", 3000, 6);
        PlayerPlaySound(playerid, 1145, 0.0, 0.0, 0.0);

        new file4[40];
        format(file4, sizeof(file4), HPATH, id);
        new INI:File = INI_Open(file4);
        INI_SetTag(File,"data");
        INI_WriteInt(File,"hLocked", HouseInfo[id][hLocked]);
        INI_Close(File);
    }
    else
    {
        HouseInfo[id][hLocked] = 1;
        GameTextForPlayer(playerid, "~w~house ~r~ LOCKED", 3000, 6);
        PlayerPlaySound(playerid, 1145, 0.0, 0.0, 0.0);

        new file4[40];
        format(file4, sizeof(file4), HPATH, id);
        new INI:File = INI_Open(file4);
        INI_SetTag(File,"data");
        INI_WriteInt(File,"hLocked", HouseInfo[id][hLocked]);
        INI_Close(File);
    }
    return 1;
}

CMD:agotohouse(playerid, params[])
{
    new id, str[144];

    if(sscanf(params, "d", id)) return SendClientMessage(playerid, COLOR_GREY, "[Usage]: /agotohouse [id] (street number is the ID)");

    SetPlayerPos(playerid, HouseInfo[id][hEntranceX], HouseInfo[id][hEntranceY], HouseInfo[id][hEntranceZ]);
    format(str, sizeof(str), "AdmCmd: You have succesfully teleported to house id %d.", id);
	SCM(playerid, COLOR_LIGHTRED, str);
    return 1;
}

CMD:buyhouse(playerid, params[])
{

    new
	id = IsPlayerNearHouseEnt(playerid);
	new string[144];
	
 	if(PlayerInfo[playerid][HouseID] != 0) return SendClientMessage(playerid, COLOR_LIGHTRED, "You already own a house.");

    if(id == -1 || id == 0) return SendClientMessage(playerid, COLOR_LIGHTRED, "[Error]: You are not near a buyable house.");

    if(HouseInfo[id][hOwned] != 0 || HouseInfo[id][hPrice] == 0) return SendClientMessage(playerid, COLOR_LIGHTRED, "[Error]: This house is not for sale.");

    if(GetPlayerCash(playerid) < HouseInfo[id][hPrice]) return SendClientMessage(playerid, COLOR_LIGHTRED, "[Error]: You don't have enough money.");

    PlayerInfo[playerid][HouseID] = id;
    GivePlayerCash(playerid, -HouseInfo[id][hPrice]);

    HouseInfo[id][hLocked] = 0;
    HouseInfo[id][hOwned] = 1;
    HouseInfo[id][hOwner] = GetName(playerid);

    SendClientMessage(playerid, COLOR_GOLD, "* Congratulations on your new house!");

    format(string,sizeof(string),""COL_BROWN"Owner: "COL_WHITE"%s\n"COL_BROWN"Street Number: "COL_WHITE"%d", HouseInfo[id][hOwner], id);
	Update3DTextLabelText(HouseInfo[id][hDLabel], 0xFFFFFFFF, string);
	
	DestroyDynamicPickup(HouseInfo[id][hOutsideIcon]);
 	HouseInfo[id][hOutsideIcon] = CreateDynamicPickup(1272, 1, HouseInfo[id][hEntranceX], HouseInfo[id][hEntranceY], HouseInfo[id][hEntranceZ], HouseInfo[id][hWorld]);

    new file4[40];
    format(file4, sizeof(file4), HPATH, id);
    new INI:File = INI_Open(file4);
    INI_SetTag(File,"data");
    INI_WriteInt(File,"hOwned", HouseInfo[id][hOwned]);
    INI_WriteInt(File,"hPrice", HouseInfo[id][hPrice]);
    INI_WriteString(File,"hOwner", HouseInfo[id][hOwner]);
    INI_WriteInt(File,"hLocked", HouseInfo[id][hLocked]);
    INI_WriteInt(File,"hMoney", HouseInfo[id][hMoney]);
    INI_WriteFloat(File,"hEntranceX", HouseInfo[id][hEntranceX]);
    INI_WriteFloat(File,"hEntranceY", HouseInfo[id][hEntranceY]);
    INI_WriteFloat(File,"hEntranceZ", HouseInfo[id][hEntranceZ]);
    INI_WriteFloat(File,"hEntranceA", HouseInfo[id][hEntranceA]);
    INI_WriteFloat(File,"hExitX", HouseInfo[id][hExitX]);
    INI_WriteFloat(File,"hExitY", HouseInfo[id][hExitY]);
    INI_WriteFloat(File,"hExitZ", HouseInfo[id][hExitZ]);
    INI_WriteFloat(File,"hExitA", HouseInfo[id][hExitA]);
    INI_WriteInt(File,"hInt", HouseInfo[id][hInt]);
    INI_WriteInt(File,"hWorld", HouseInfo[id][hWorld]);
    INI_WriteInt(File,"hInsideInt", HouseInfo[id][hInsideInt]);
    INI_WriteInt(File,"hInsideWorld", HouseInfo[id][hInsideWorld]);
    INI_Close(File);
    return 1;
}

CMD:asellhouse(playerid, params[])
{
    new id = IsPlayerNearHouseEnt(playerid);
	new string[144];
    if(PlayerInfo[playerid][pAdmin] < 3) return SCM(playerid, COLOR_GREY,"[Error]: You're not authorized to use this command.");
    if(HouseInfo[id][hOwned] == 0) return SCM(playerid, COLOR_LIGHTRED,"[Error]: This house is not owned by anyone.");
    HouseInfo[id][hOwned] = 0;
    HouseInfo[id][hOwner] = 0;
    HouseInfo[id][hLocked] = 1;
    SCM(playerid, COLOR_LIGHTRED, "AdmCmd: You have succesfully admin-sold this house.");

 	format(string,sizeof(string),""COL_BROWN"Owner: "COL_WHITE"None\n"COL_BROWN"Price: "COL_WHITE"$%d\n"COL_BROWN"Street Number: "COL_WHITE"%d", HouseInfo[id][hPrice], id);
	Update3DTextLabelText(HouseInfo[id][hDLabel], 0xFFFFFFFF, string);
	
 	if(HouseInfo[id][hOutsideIcon]) DestroyDynamicPickup(HouseInfo[id][hOutsideIcon]);
    HouseInfo[id][hOutsideIcon] = CreateDynamicPickup(1273, 1, HouseInfo[id][hEntranceX], HouseInfo[id][hEntranceY], HouseInfo[id][hEntranceZ], HouseInfo[id][hWorld]);

    new file4[40];
    format(file4, sizeof(file4), HPATH, id);
    new INI:File = INI_Open(file4);
    INI_SetTag(File,"data");
    INI_WriteInt(File,"hOwned", HouseInfo[id][hOwned]);
    INI_WriteInt(File,"hPrice", HouseInfo[id][hPrice]);
    INI_WriteString(File,"hOwner", HouseInfo[id][hOwner]);
    INI_WriteInt(File,"hLocked", HouseInfo[id][hLocked]);
    INI_WriteInt(File,"hMoney", HouseInfo[id][hMoney]);
    INI_WriteFloat(File,"hEntranceX", HouseInfo[id][hEntranceX]);
    INI_WriteFloat(File,"hEntranceY", HouseInfo[id][hEntranceY]);
    INI_WriteFloat(File,"hEntranceZ", HouseInfo[id][hEntranceZ]);
    INI_WriteFloat(File,"hEntranceA", HouseInfo[id][hEntranceA]);
    INI_WriteFloat(File,"hExitX", HouseInfo[id][hExitX]);
    INI_WriteFloat(File,"hExitY", HouseInfo[id][hExitY]);
    INI_WriteFloat(File,"hExitZ", HouseInfo[id][hExitZ]);
    INI_WriteFloat(File,"hExitA", HouseInfo[id][hExitA]);
    INI_WriteInt(File,"hInt", HouseInfo[id][hInt]);
    INI_WriteInt(File,"hWorld", HouseInfo[id][hWorld]);
    INI_WriteInt(File,"hInsideInt", HouseInfo[id][hInsideInt]);
    INI_WriteInt(File,"hInsideWorld", HouseInfo[id][hInsideWorld]);
    INI_Close(File);
    return 1;
}

CMD:sellhouse(playerid, params[])
{
    new
	id2 = PlayerInfo[playerid][HouseID];

	new string[144];

    if(PlayerInfo[playerid][HouseID] == 0) return SCM(playerid, COLOR_LIGHTRED, "[Error]: You do not own a business.");
    HouseInfo[id2][hOwned] = 0;
    HouseInfo[id2][hOwner] = 0;
    HouseInfo[id2][hLocked] = 1;

    GivePlayerCash(playerid, HouseInfo[id2][hPrice]);
    PlayerInfo[playerid][HouseID] = 0;
    SCM(playerid, COLOR_GOLD, "* You have succesfully sold your house. Sad to see it go.");

 	format(string,sizeof(string),""COL_BROWN"Owner: "COL_WHITE"None\n"COL_BROWN"Price: "COL_WHITE"$%d\n"COL_BROWN"Street Number: "COL_WHITE"%d", HouseInfo[id2][hPrice], id2);
	Update3DTextLabelText(HouseInfo[id2][hDLabel], 0xFFFFFFFF, string);
	
 	if(HouseInfo[id2][hOutsideIcon]) DestroyDynamicPickup(HouseInfo[id2][hOutsideIcon]);
    HouseInfo[id2][hOutsideIcon] = CreateDynamicPickup(1273, 1, HouseInfo[id2][hEntranceX], HouseInfo[id2][hEntranceY], HouseInfo[id2][hEntranceZ], HouseInfo[id2][hWorld]);
	
    new file4[40];
    format(file4, sizeof(file4), HPATH, id2);
    new INI:File = INI_Open(file4);
    INI_SetTag(File,"data");
    INI_WriteInt(File,"hOwned", HouseInfo[id2][hOwned]);
    INI_WriteInt(File,"hPrice", HouseInfo[id2][hPrice]);
    INI_WriteString(File,"hOwner", HouseInfo[id2][hOwner]);
    INI_WriteInt(File,"hLocked", HouseInfo[id2][hLocked]);
    INI_WriteInt(File,"hMoney", HouseInfo[id2][hMoney]);
    INI_WriteFloat(File,"hEntranceX", HouseInfo[id2][hEntranceX]);
    INI_WriteFloat(File,"hEntranceY", HouseInfo[id2][hEntranceY]);
    INI_WriteFloat(File,"hEntranceZ", HouseInfo[id2][hEntranceZ]);
    INI_WriteFloat(File,"hEntranceA", HouseInfo[id2][hEntranceA]);
    INI_WriteFloat(File,"hExitX", HouseInfo[id2][hExitX]);
    INI_WriteFloat(File,"hExitY", HouseInfo[id2][hExitY]);
    INI_WriteFloat(File,"hExitZ", HouseInfo[id2][hExitZ]);
    INI_WriteFloat(File,"hExitA", HouseInfo[id2][hExitA]);
    INI_WriteInt(File,"hInt", HouseInfo[id2][hInt]);
    INI_WriteInt(File,"hWorld", HouseInfo[id2][hWorld]);
    INI_WriteInt(File,"hInsideInt", HouseInfo[id2][hInsideInt]);
    INI_WriteInt(File,"hInsideWorld", HouseInfo[id2][hInsideWorld]);
    INI_Close(File);
    return 1;
}

CMD:createhouse(playerid, params[])
{
	new
	price, id, int, world, string[144], Float:Xi,
	Float:Yi, Float:Zi, inti, Float:X,Float:Y,Float:Z,Float:A;

    if(PlayerInfo[playerid][pAdmin] < 4) return SCM(playerid, COLOR_GREY,"[Error]: You're not authorized to use this command.");
    if(sscanf(params, "ddfff", price, inti, Xi, Yi, Zi)) return SendClientMessage(playerid, COLOR_GREY, "[Usage]: /createhouse [price] [interior] [X] [Y] [Z]");

    if(price < 4000) return SendClientMessage(playerid, COLOR_LIGHTRED, "[Error]: Price cannot go below $4,000.");

    for(new h = 1;h < sizeof(HouseInfo);h++)
    {
        if(HouseInfo[h][hPrice] == 0)
        {
            id = h;
            break;
        }
    }

    GetPlayerPos(playerid, X, Y, Z);
    GetPlayerFacingAngle(playerid, A);
    int = GetPlayerInterior(playerid);
    world = GetPlayerVirtualWorld(playerid);
    HouseInfo[id][hInsideInt] = inti;
    HouseInfo[id][hExitX] = Xi;
    HouseInfo[id][hExitY] = Yi;
    HouseInfo[id][hExitZ] = Zi;

    HouseInfo[id][hOwned] = 0;
    HouseInfo[id][hPrice] = price;
    HouseInfo[id][hEntranceX] = X;
    HouseInfo[id][hEntranceY] = Y;
    HouseInfo[id][hEntranceZ] = Z;
    HouseInfo[id][hEntranceA] = A;
    HouseInfo[id][hLocked] = 1;

   	format(string,sizeof(string),""COL_BROWN"Owner: "COL_WHITE"None\n"COL_BROWN"Price: "COL_WHITE"$%d\n"COL_BROWN"Street Number: "COL_WHITE"%d", HouseInfo[id][hPrice], id);
	HouseInfo[id][hDLabel] = Create3DTextLabel(string, 0xFFFFFF, X, Y, Z, 10.0, 0, 0);

    HouseInfo[id][hInt] =int;
    HouseInfo[id][hWorld] =world;
    HouseInfo[id][hInsideWorld] =id;
    OnPlayerUpdate(playerid);

    format(string, sizeof(string), "None");
    strmid(BusinessInfo[id][bName], string, 0, strlen(string), 255);

    if(HouseInfo[id][hOutsideIcon]) DestroyDynamicPickup(HouseInfo[id][hOutsideIcon]);
    HouseInfo[id][hOutsideIcon] = CreateDynamicPickup(1273, 1, HouseInfo[id][hEntranceX], HouseInfo[id][hEntranceY], HouseInfo[id][hEntranceZ], HouseInfo[id][hWorld]);
    new file4[40];
    format(file4, sizeof(file4), HPATH, id);
    new INI:File = INI_Open(file4);
    INI_SetTag(File,"data");
    INI_WriteInt(File,"hOwned", HouseInfo[id][hOwned]);
    INI_WriteInt(File,"hPrice", HouseInfo[id][hPrice]);
    INI_WriteString(File,"hOwner", HouseInfo[id][hOwner]);
    INI_WriteInt(File,"hLocked", HouseInfo[id][hLocked]);
    INI_WriteInt(File,"hMoney", HouseInfo[id][hMoney]);
    INI_WriteFloat(File,"hEntranceX", HouseInfo[id][hEntranceX]);
    INI_WriteFloat(File,"hEntranceY", HouseInfo[id][hEntranceY]);
    INI_WriteFloat(File,"hEntranceZ", HouseInfo[id][hEntranceZ]);
    INI_WriteFloat(File,"hEntranceA", HouseInfo[id][hEntranceA]);
    INI_WriteFloat(File,"hExitX", HouseInfo[id][hExitX]);
    INI_WriteFloat(File,"hExitY", HouseInfo[id][hExitY]);
    INI_WriteFloat(File,"hExitZ", HouseInfo[id][hExitZ]);
    INI_WriteFloat(File,"hExitA", HouseInfo[id][hExitA]);
    INI_WriteInt(File,"hInt", HouseInfo[id][hInt]);
    INI_WriteInt(File,"hWorld", HouseInfo[id][hWorld]);
    INI_WriteInt(File,"hInsideInt", HouseInfo[id][hInsideInt]);
    INI_WriteInt(File,"hInsideWorld", HouseInfo[id][hInsideWorld]);
    INI_Close(File);
    return 1;
}

CMD:deletehouse(playerid, params[])
{
    new
	id = IsPlayerNearHouseEnt(playerid);
 	if(PlayerInfo[playerid][pAdmin] < 3) return SCM(playerid, COLOR_GREY,"[Error]: You're not authorized to use this command.");
 	if(HouseInfo[id][hOwned] == 1) return SCM(playerid, COLOR_LIGHTRED, "* This house is owned.");

    HouseInfo[id][hOwned] = 0;
    HouseInfo[id][hPrice] = 0;
    HouseInfo[id][hOwner] = 0;
    HouseInfo[id][hLocked] = 0;
    HouseInfo[id][hMoney] = 0;
    HouseInfo[id][hEntranceX] = 0;
    HouseInfo[id][hEntranceY] = 0;
    HouseInfo[id][hEntranceZ] = 0;
    HouseInfo[id][hEntranceA] = 0;
    HouseInfo[id][hExitX] = 0;
    HouseInfo[id][hExitY] = 0;
    HouseInfo[id][hExitZ] = 0;
    HouseInfo[id][hExitA] = 0;
    HouseInfo[id][hInt] = 0;
    HouseInfo[id][hWorld] = 0;

    Delete3DTextLabel(HouseInfo[id][hDLabel]);

	DestroyDynamicPickup(HouseInfo[id][hOutsideIcon]);

    OnPlayerUpdate(playerid);

    new string[64];

    format(string, sizeof(string), HPATH, id);
    fremove(string);
    return 1;
}

CMD:housebalance(playerid, params[])
{
	new
	str[64], id = IsPlayerInsideHouse(playerid);

	if(id != PlayerInfo[playerid][HouseID]) return SCM(playerid, COLOR_LIGHTRED, "[Error]: You do not own this house.");
 	if(PlayerInfo[playerid][HouseID] == 0) return SCM(playerid, COLOR_LIGHTRED, "[Error]: You do not own a house!");
	format(str, sizeof(str), "You have $%d in your house vault.", HouseInfo[PlayerInfo[playerid][HouseID]][hMoney]);
	SCM(playerid, COLOR_GOLD, str);
    return 1;
}

CMD:housedeposit(playerid,params[])
{
    new
	string[64], amount, id = IsPlayerInsideHouse(playerid);
	
	if(id != PlayerInfo[playerid][HouseID]) return SCM(playerid, COLOR_LIGHTRED, "[Error]: You do not own this house.");
 	if(PlayerInfo[playerid][HouseID] == 0) return SCM(playerid, COLOR_LIGHTRED, "[Error]: You do not own a house!");
	if(sscanf(params, "d", amount)) return SendClientMessage(playerid, -1, "[Usage]: /housedeposit [amount]");
 	if (amount > GetPlayerCash(playerid)) return SendClientMessage(playerid, COLOR_LIGHTRED, "[Error]: You do not have that much money.");

	GivePlayerCash(playerid, -amount);
	HouseInfo[id][hMoney] += amount;
	format(string, sizeof(string), "HOUSE: You have successfully deposited $%d to your house vault.", amount);
	SendClientMessage(playerid, COLOR_GOLD, string);
 	return 1;
}

CMD:housewithdraw(playerid,params[])
{
    new
	string[128], amount, id = IsPlayerInsideHouse(playerid);

	if(id != PlayerInfo[playerid][HouseID]) return SCM(playerid, COLOR_LIGHTRED, "[Error]: You do not own this house.");
 	if(PlayerInfo[playerid][HouseID] == 0) return SCM(playerid, COLOR_LIGHTRED, "[Error]: You do not own a house!");
	if(sscanf(params, "d", amount)) return SendClientMessage(playerid, -1, "[Usage]: /housewithdraw [amount]");
 	if (amount > HouseInfo[id][hMoney]) return SendClientMessage(playerid, COLOR_LIGHTRED, "[Error]: You do not have that much money in your house vault.");

	GivePlayerCash(playerid, amount);
	HouseInfo[id][hMoney] -= amount;
	format(string, sizeof(string), "HOUSE: You have successfully withdrawn $%d from your house vault.", amount);
	SendClientMessage(playerid, COLOR_GOLD, string);
 	return 1;
}

CMD:buybiz(playerid, params[])
{

    new
	id = IsPlayerNearBizEnt(playerid);
	new biztext[24];
	new string[128];
	
 	if(PlayerInfo[playerid][BizID] != 0) return SendClientMessage(playerid, COLOR_LIGHTRED, "You already own a business.");
	
    if(id == -1 || id == 0) return SendClientMessage(playerid, COLOR_LIGHTRED, "[Error]: You are not near a buyable business.");

    if(BusinessInfo[id][bOwned] != 0 || BusinessInfo[id][bPrice] == 0) return SendClientMessage(playerid, COLOR_LIGHTRED, "[Error]: This business is not for sale.");

    if(GetPlayerCash(playerid) < BusinessInfo[id][bPrice]) return SendClientMessage(playerid, COLOR_LIGHTRED, "[Error]: You don't have enough money.");

    PlayerInfo[playerid][BizID] = id;
    GivePlayerCash(playerid, -BusinessInfo[id][bPrice]);

    BusinessInfo[id][bLocked] = 0;
    BusinessInfo[id][bOwned] = 1;
    BusinessInfo[id][bOwner] = GetName(playerid);

    SendClientMessage(playerid, COLOR_GOLD, "* Congratulations on your new business! Change the name of the business with /bizname.");
    
   	switch(BusinessInfo[id][bType])
    {
 			case 20: biztext = "Dealership";
 			case 19: biztext = "Electronic Store";
   			case 18: biztext = "Ammunition";
   			case 17: biztext = "Gym";
   			case 16: biztext = "Hotel";
   			case 15: biztext = "Motel";
   			case 14: biztext = "Diner";
         	case 13: biztext = "Tattoo Store";
         	case 12: biztext = "Barbershop";
            case 11: biztext = "Flower Store";
           	case 10: biztext = "98 Cents";
    		case 9: biztext = "69 Cents";
            case 8: biztext = "Liqour Store";
	    	case 7: biztext = "Restaurant";
	    	case 6: biztext = "Bank";
	    	case 5: biztext = "Hospital";
	        case 4: biztext = "Police Station";
	        case 3: biztext = "24/7";
	        case 2: biztext = "Club";
	        case 1: biztext = "Bar";
	        case 0: biztext = "Clothes Shop";
    }
    
    format(string,sizeof(string),""COL_BROWN"Owner: "COL_WHITE"%s\n"COL_BROWN"Name: "COL_WHITE"%s\n"COL_BROWN"Type: "COL_WHITE"%s\n"COL_BROWN"Street Number: "COL_WHITE"%d", BusinessInfo[id][bOwner], BusinessInfo[id][bName], biztext, id);
	Update3DTextLabelText(BusinessInfo[id][DLabel], 0xFFFFFFFF, string);

	new file4[40];
	format(file4, sizeof(file4), BPATH, id);
	new INI:File = INI_Open(file4);
	INI_SetTag(File,"data");
	INI_WriteInt(File,"bOwned", BusinessInfo[id][bOwned]);
	INI_WriteInt(File,"bPrice", BusinessInfo[id][bPrice]);
	INI_WriteString(File,"bOwner", BusinessInfo[id][bOwner]);
	INI_WriteInt(File,"bType", BusinessInfo[id][bType]);
	INI_WriteInt(File,"bLocked", BusinessInfo[id][bLocked]);
	INI_WriteInt(File,"bMoney", BusinessInfo[id][bMoney]);
	INI_WriteFloat(File,"bEntranceX", BusinessInfo[id][bEntranceX]);
	INI_WriteFloat(File,"bEntranceY", BusinessInfo[id][bEntranceY]);
	INI_WriteFloat(File,"bEntranceZ", BusinessInfo[id][bEntranceZ]);
	INI_WriteFloat(File,"bEntranceA", BusinessInfo[id][bEntranceA]);
	INI_WriteFloat(File,"bExitX", BusinessInfo[id][bExitX]);
	INI_WriteFloat(File,"bExitY", BusinessInfo[id][bExitY]);
	INI_WriteFloat(File,"bExitZ", BusinessInfo[id][bExitZ]);
	INI_WriteFloat(File,"bExitA", BusinessInfo[id][bExitA]);
	INI_WriteInt(File,"bInt", BusinessInfo[id][bInt]);
	INI_WriteInt(File,"bWorld", BusinessInfo[id][bWorld]);
	INI_WriteInt(File,"bInsideInt", BusinessInfo[id][bInsideInt]);
	INI_WriteInt(File,"bInsideWorld", BusinessInfo[id][bInsideWorld]);
	INI_WriteString(File,"bName", BusinessInfo[id][bName]);
	INI_Close(File);
    return 1;
}

CMD:bizwithdraw(playerid, params[])
{
	new
	amount, id = IsPlayerInsideBiz(playerid);
	
	if(id != PlayerInfo[playerid][BizID]) return SCM(playerid, COLOR_LIGHTRED, "[Error]: You do not own this business.");
 	if(PlayerInfo[playerid][BizID] == 0) return SCM(playerid, COLOR_LIGHTRED, "[Error]: You do not own a business!");
    if(sscanf(params, "d", amount)) return SCM(playerid, COLOR_GREY, "[Usage]: /bizwithdraw [amount]");
    if (amount > BusinessInfo[PlayerInfo[playerid][BizID]][bMoney]) return SCM(playerid, COLOR_LIGHTRED, "[Error]: Your business does not contain that much money.");
    
	GivePlayerCash(playerid, amount);
	BusinessInfo[PlayerInfo[playerid][BizID]][bMoney] = -amount;
	
	new file4[40];
	format(file4, sizeof(file4), BPATH, id);
	new INI:File = INI_Open(file4);
	INI_SetTag(File,"data");
	INI_WriteInt(File,"bOwned", BusinessInfo[id][bOwned]);
	INI_WriteInt(File,"bPrice", BusinessInfo[id][bPrice]);
	INI_WriteString(File,"bOwner", BusinessInfo[id][bOwner]);
	INI_WriteInt(File,"bType", BusinessInfo[id][bType]);
	INI_WriteInt(File,"bLocked", BusinessInfo[id][bLocked]);
	INI_WriteInt(File,"bMoney", BusinessInfo[id][bMoney]);
	INI_WriteFloat(File,"bEntranceX", BusinessInfo[id][bEntranceX]);
	INI_WriteFloat(File,"bEntranceY", BusinessInfo[id][bEntranceY]);
	INI_WriteFloat(File,"bEntranceZ", BusinessInfo[id][bEntranceZ]);
	INI_WriteFloat(File,"bEntranceA", BusinessInfo[id][bEntranceA]);
	INI_WriteFloat(File,"bExitX", BusinessInfo[id][bExitX]);
	INI_WriteFloat(File,"bExitY", BusinessInfo[id][bExitY]);
	INI_WriteFloat(File,"bExitZ", BusinessInfo[id][bExitZ]);
	INI_WriteFloat(File,"bExitA", BusinessInfo[id][bExitA]);
	INI_WriteInt(File,"bInt", BusinessInfo[id][bInt]);
	INI_WriteInt(File,"bWorld", BusinessInfo[id][bWorld]);
	INI_WriteInt(File,"bInsideInt", BusinessInfo[id][bInsideInt]);
	INI_WriteInt(File,"bInsideWorld", BusinessInfo[id][bInsideWorld]);
	INI_WriteString(File,"bName", BusinessInfo[id][bName]);
	INI_Close(File);
    return 1;
}

CMD:bizbalance(playerid, params[])
{
	new
	str[64], id = IsPlayerInsideBiz(playerid);
	
	if(id != PlayerInfo[playerid][BizID]) return SCM(playerid, COLOR_LIGHTRED, "[Error]: You do not own this business.");
 	if(PlayerInfo[playerid][BizID] == 0) return SCM(playerid, COLOR_LIGHTRED, "[Error]: You do not own a business!");
	format(str, sizeof(str), "You have $%d in your business vault.", BusinessInfo[PlayerInfo[playerid][BizID]][bMoney]);
	SCM(playerid, COLOR_GOLD, str);
    return 1;
}


CMD:clothes(playerid, params[])
{
    new
	id = IsPlayerInsideBiz(playerid);
	
    if(GetPlayerCash(playerid) < 100) return SCM(playerid, COLOR_LIGHTRED, "[Error]: You do not have enough money. ($100)");
    if(BusinessInfo[InsideBiz[playerid]][bType] != 0) return SCM(playerid, COLOR_LIGHTRED, "[Error]: You need to be in a clothing shop.");
    
    GivePlayerCash(playerid, -100);
    BusinessInfo[id][bMoney] = 100;
    
	new file4[40];
	format(file4, sizeof(file4), BPATH, id);
	new INI:File = INI_Open(file4);
	INI_SetTag(File,"data");
	INI_WriteInt(File,"bOwned", BusinessInfo[id][bOwned]);
	INI_WriteInt(File,"bPrice", BusinessInfo[id][bPrice]);
	INI_WriteString(File,"bOwner", BusinessInfo[id][bOwner]);
	INI_WriteInt(File,"bType", BusinessInfo[id][bType]);
	INI_WriteInt(File,"bLocked", BusinessInfo[id][bLocked]);
	INI_WriteInt(File,"bMoney", BusinessInfo[id][bMoney]);
	INI_WriteFloat(File,"bEntranceX", BusinessInfo[id][bEntranceX]);
	INI_WriteFloat(File,"bEntranceY", BusinessInfo[id][bEntranceY]);
	INI_WriteFloat(File,"bEntranceZ", BusinessInfo[id][bEntranceZ]);
	INI_WriteFloat(File,"bEntranceA", BusinessInfo[id][bEntranceA]);
	INI_WriteFloat(File,"bExitX", BusinessInfo[id][bExitX]);
	INI_WriteFloat(File,"bExitY", BusinessInfo[id][bExitY]);
	INI_WriteFloat(File,"bExitZ", BusinessInfo[id][bExitZ]);
	INI_WriteFloat(File,"bExitA", BusinessInfo[id][bExitA]);
	INI_WriteInt(File,"bInt", BusinessInfo[id][bInt]);
	INI_WriteInt(File,"bWorld", BusinessInfo[id][bWorld]);
	INI_WriteInt(File,"bInsideInt", BusinessInfo[id][bInsideInt]);
	INI_WriteInt(File,"bInsideWorld", BusinessInfo[id][bInsideWorld]);
	INI_WriteString(File,"bName", BusinessInfo[id][bName]);
	INI_Close(File);
	return 1;
}

CMD:dropcigarette(playerid, params[])
{
    if(IsSmokingCigarette[playerid] == 0) return SCM(playerid, COLOR_LIGHTRED, "[Error]: You're not smoking a cigarette.");
    
    IsSmokingCigarette[playerid] = 0;
    PlayerActionMessage(playerid,15.0,"drop his cigarette on the ground.");
    return 1;
}

CMD:deposit(playerid,params[])
{
    new
	string[64], amount;

	if(sscanf(params, "d", amount)) return SendClientMessage(playerid, -1, "[Usage]: /deposit [amount]");
 	if (amount > GetPlayerCash(playerid)) return SendClientMessage(playerid, COLOR_LIGHTRED, "[Error]: You do not have that much money.");
 	if(IsPlayerInRangeOfPoint(playerid, 10.0, 2316.6206,-15.2233,26.7422))
	{
		GivePlayerCash(playerid, -amount);
		PlayerInfo[playerid][pBankAccount] += amount;
		format(string, sizeof(string), "BANK: You have successfully deposited $%d to your bank account.", amount);
		SendClientMessage(playerid, COLOR_GOLD, string);
 	} else return SCM(playerid, COLOR_LIGHTRED, "[Error]: You're not at the bank.");
 	return 1;
}

CMD:withdraw(playerid,params[])
{
    new
	string[64], amount;

	if(sscanf(params, "d", amount)) return SendClientMessage(playerid, -1, "[USAGE]: /withdraw [amount]");
	if (amount > PlayerInfo[playerid][pBankAccount]) return SendClientMessage(playerid, COLOR_LIGHTRED, "[Error]: You do not have that much money in your bank.");
 	if(IsPlayerInRangeOfPoint(playerid, 10.0, 2316.6206,-15.2233,26.7422))
	{
		PlayerInfo[playerid][pBankAccount] -= amount;
		GivePlayerCash(playerid, amount);
		format(string, sizeof(string), "BANK: You have successfully withdrawn $%d from your bank account.", amount);
		SendClientMessage(playerid, COLOR_GOLD, string);
	} else return SCM(playerid, COLOR_LIGHTRED, "[Error]: You're not at the bank.");
	return 1;
}

CMD:balance(playerid,params[])
{
    new
	string[64];

   	if(IsPlayerInRangeOfPoint(playerid, 10.0, 2316.6206,-15.2233,26.7422))
	{
	    format(string, sizeof(string), "BANK: You currently have $%d In your bank account.", PlayerInfo[playerid][pBankAccount]);
	    SendClientMessage(playerid,COLOR_GOLD,string);
	} else return SCM(playerid, COLOR_LIGHTRED, "[Error]: You're not at the bank.");
	return 1;
}

CMD:mask(playerid,params[])
{
	if(PlayerInfo[playerid][pMask] == 1)
	{
		if(MaskOn[playerid] == 0)
		{
	        MaskOn[playerid] = 1;
	        GameTextForPlayer(playerid, "~p~MASK ON", 5000, 3);
	        for(new i = 0; i < MAX_PLAYERS; i++) ShowPlayerNameTagForPlayer(i, playerid, false);

		    new Float:X, Float:Y, Float:Z;
		    GetPlayerPos( playerid, X, Y, Z );
		    new string[64];
		    format(string,sizeof(string),"Stranger_%d%d", playerid, masknumber[playerid]);
		    NameTag[playerid] = Create3DTextLabel(string, -1, X, Y, Z, 15.0, 0, 0);
	    	Attach3DTextLabelToPlayer(NameTag[playerid], playerid, 0.0, 0.0, 0.7);
		}
		else if(MaskOn[playerid] == 1)
		{
	        MaskOn[playerid] = 0;
	        GameTextForPlayer(playerid, "~p~MASK OFF", 5000, 3);
	        for(new i = 0; i < MAX_PLAYERS; i++) ShowPlayerNameTagForPlayer(i, playerid, true);
	        Delete3DTextLabel(NameTag[playerid]);
		}
	} else return SCM(playerid, COLOR_LIGHTRED, "* You do not have a mask.");
	return 1;
}

CMD:pm(playerid, params[])
{
    new
	PID, message[144], string[144];
    
    if(sscanf(params, "us[144]", PID, message)) return SCM(playerid, COLOR_GREY, "[Usage]: /PM  [PlayerID] [message].");
    if(!IsPlayerConnected(PID)) return SCM(playerid, COLOR_LIGHTRED, "[Error]: That player is not connected.");
    if (playerid == PID) return SendClientMessage(playerid, COLOR_LIGHTRED,"[Error]: You can't PM yourself.");
    
    format(string, sizeof(string), "(( PM From: %s(%d): %s ))", GetName(playerid), playerid, message);
    SendClientMessage(PID, COLOR_YELLOW, string);
    format(string, sizeof(string), "(( PM Sent: %s(%d): %s ))", GetName(PID), PID, message);
    SendClientMessage(playerid, COLOR_YELLOW, string);
    PlayerPlaySound(PID,1085,0.0,0.0,0.0);
    return 1;
}

CMD:ame(playerid, params[])
{
	new
	string[144], str[144], message[144];
      
    if(sscanf(params, "s[144]", message)) return SCM(playerid, COLOR_GREY, "[Usage]: /ame [message]");
    
    SetPlayerChatBubble(playerid, params, COLOR_PURPLE, 75.0, 1000);
    format(string, sizeof(string), "> %s %s", GetName(playerid), message);
    SendClientMessage(playerid, COLOR_PURPLE, string);
    format(str, sizeof(str), "%s %s", GetName(playerid), message);
    SetPlayerChatBubble(playerid, string, COLOR_PURPLE, 75.0, 6000);
	return 1;
}

CMD:sms(playerid, params[])
{
	new
	string[144], smstext[144], tnum;
      
    new sender = PlayerInfo[playerid][pNumber];
	if(sscanf(params, "ds[144]", tnum, smstext)) return SCM(playerid, COLOR_GREY, "[Usage]: /sms [number] [message].");
	
	format(string, sizeof(string), "* %s takes out a cellphone.", GetName(playerid));
	ProxDetector(30.0, playerid, string,COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE);
	
	for(new i = 0; i < MAX_PLAYERS; i++)
	if(IsPlayerConnected(i))
	if(PlayerInfo[i][pNumber] == tnum)
	{
		if(onoff[i] == 0) return SCM(playerid, COLOR_LIGHTRED, "* You hear a busy tone...");
		format(string, sizeof(string), "SMS: %s, Sender: %s (%d)", smstext,GetName(playerid),sender);
		SCM(i, COLOR_YELLOW, string);
		PlayerPlaySound(i, 1052, 0.0, 0.0, 0.0);
		SendClientMessage(playerid, COLOR_YELLOW, "* Text message sucessfully sent.");
	} else return SendClientMessage(playerid, COLOR_LIGHTRED, "* Text message failed...");
	return 1;
}

CMD:call(playerid, params[])
{
	new
	tnum, string[64];
   	
  	new sender = PlayerInfo[playerid][pNumber];
  	if(sscanf(params, "d", tnum)) SendClientMessage(playerid, COLOR_GREY, "[Usage]: /call [number]");

	SetPlayerSpecialAction(playerid,SPECIAL_ACTION_USECELLPHONE);
	format(string, sizeof(string), "* %s takes out a cellphone.", GetName(playerid));
	ProxDetector(30.0, playerid, string,COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE);

  

	for(new i = 0; i <= MAX_PLAYERS; i++)
 	{
  		if(IsPlayerConnected(i))
    	{
     		if(PlayerInfo[i][pNumber] == tnum)
  			{
    			if(onoff[i] == 0) return SCM(playerid, COLOR_LIGHTRED, "* That cellphone is turned off...");
				if(oncall[i] == 1) return SCM(playerid, COLOR_LIGHTRED, "* You get a busy tone...");
				if(iscalled[i] == 1) return SCM(playerid, COLOR_LIGHTRED, "* You get a busy tone...");
				
				Mobile[playerid] = i;

				format(string, sizeof(string), "* Your phone is ringing. (/Pickup) Caller: %d", sender);
				SendClientMessage(i, COLOR_YELLOW, string);

				format(string, sizeof(string), "* %s's phone begins to ring.", GetName(i));
				ProxDetector(30.0, playerid, string,COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE);
				
				SetPlayerSpecialAction(playerid,SPECIAL_ACTION_USECELLPHONE);

				PlayerPlaySound(playerid, 3600, 0.0, 0.0, 0.0);
				PlayerPlaySound(i, 3600, 0.0, 0.0, 0.0);
				iscalled[i] = 1;

			}
		}
	}
	return 1;
}

CMD:pickup(playerid, params[])
{
	new
	string[64];
	
	if(iscalled[playerid] == 0) return SCM(playerid, COLOR_LIGHTRED, "[Error]: Your phone is not ringing.");
	for(new i = 0; i <= MAX_PLAYERS; i++)
	{
 		if(IsPlayerConnected(i) == 1)
   		{
     		if(Mobile[i] == playerid)
       		{
		         Mobile[playerid] = i;
		         SendClientMessage(i,  COLOR_GOLD, "* They have picked up the call.");
		         SetPlayerSpecialAction(playerid,SPECIAL_ACTION_USECELLPHONE);
		         format(string, sizeof(string), "* %s answers their cellphone.", GetName(playerid));
		         ProxDetector(30.0, playerid, string,COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE);
		         oncall[playerid] = 1;
		         oncall[i] = 1;
       			 }
			}
   		}
	return 1;
}

COMMAND:phone(playerid, params[])
{
    if(onoff[playerid] == 0)
	{
 		onoff[playerid] = 1;
 		SCM(playerid, COLOR_GOLD, "* You've turned your phone on.");
	}
   	else if(onoff[playerid] == 1)
	{
	    SCM(playerid, COLOR_GOLD, "* You've turned your phone off.");
   		onoff[playerid] = 0;
	}
	return 1;
}

CMD:hangup(playerid, params[])
{
	new
	string[64];
	
	for(new i = 0; i <= MAX_PLAYERS; i++)
 	{
 		if(IsPlayerConnected(i) == 1)
 		{
 			if(Mobile[i] == playerid)
 			{
			    Mobile[playerid] = i;
			    SendClientMessage(i,  COLOR_GOLD, "* They hung up.");
			    
			    format(string, sizeof(string), "* %s pockets their cellphone.", GetName(playerid));
			    ProxDetector(30.0, playerid, string,COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE);
			    
			    SetPlayerSpecialAction(playerid,SPECIAL_ACTION_STOPUSECELLPHONE);
			    oncall[playerid] = 0;
			    oncall[i] = 0;
			    iscalled[i] = 0;
			    iscalled[playerid] = 0;
       			}
			}
		}
	return 1;
}

CMD:commands(playerid, params[])
{
	SCM(playerid, COLOR_GREEN, "_______________________________"COL_WHITE"[SERVER COMMANDS]"COL_GREEN"_______________________________");
	SCM(playerid, COLOR_WHITE, "[GENERAL]: /pay /pm /use /stats /giverespect /dice /animlist /call /phone /givedrug /animlist");
	SCM(playerid, COLOR_WHITE, "[GENERAL]: /report /givegun /balance /withdraw /deposit /pickup /hangup /takedrivingtest");
	SCM(playerid, COLOR_WHITE, "[GENERAL]: /sms /dropcigarette /licenses /greet /vehiclehelp /businesshelp /househelp");
	SCM(playerid, COLOR_WHITE, "[GENERAL]: (ad)vertisement /frisk /train /buy /help /low /do /me /shout /(o)oc");
    if(IsACop(playerid))
    {
		SCM(playerid, COLOR_WHITE, "[POLICE]: /arrest /cuff /uncuff /opendoor /closedoor /locker");
		SCM(playerid, COLOR_WHITE, "[POLICE]: /revokeguns /revokedrugs /(m)egaphone /opencell /closecell");
    }
   	return 1;
}

CMD:vehiclehelp(playerid, params[])
{
	SCM(playerid, COLOR_GREEN, "_______________________________"COL_WHITE"[VEHICLE COMMANDS]"COL_GREEN"_______________________________");
	SCM(playerid, COLOR_WHITE, "[GENERAL]: /engine /vlock /trunk /trackcar /v /fix /eject /ejectall /valarm");
	SCM(playerid, COLOR_WHITE, "[GENERAL]: /mph /clearmods /sellv /givecarkeys /fuel /trunk /kph");
   	return 1;
}

CMD:househelp(playerid, params[])
{
	SCM(playerid, COLOR_GREEN, "_______________________________"COL_WHITE"[HOUSE COMMANDS]"COL_GREEN"_______________________________");
	SCM(playerid, COLOR_WHITE, "[GENERAL]: /buyhouse /lockhouse /housewithdraw /housedeposit /housebalance /sellhouse");
   	return 1;
}

CMD:businesshelp(playerid, params[])
{
	SCM(playerid, COLOR_GREEN, "_______________________________"COL_WHITE"[HOUSE COMMANDS]"COL_GREEN"_______________________________");
	SCM(playerid, COLOR_WHITE, "[GENERAL]: /buybiz /sellbiz /bizname /lockbiz /bizwithdraw /bizbalance");
   	return 1;
}

CMD:admincommands(playerid, params[])
{
	SCM(playerid, COLOR_GREEN, "_______________________________"COL_WHITE"[ADMINISTRATOR COMMANDS]"COL_GREEN"_______________________________");
	if(PlayerInfo[playerid][pAdmin] == 1)
    {
		SCM(playerid, COLOR_WHITE, "[ADMIN LVL 1]: /acceptreport /markfalse /warn /mute /unmute /freeze /unfreeze /spec /specoff");
		SCM(playerid, COLOR_WHITE, "[ADMIN LVL 1]: /gethere /goto /gethere /clearchat /aduty /(a)dminchat /announcement /agotobiz");
    }
    if(PlayerInfo[playerid][pAdmin] == 2)
    {
  	 	SCM(playerid, COLOR_WHITE, "[ADMIN LVL 1]: /acceptreport /markfalse /warn /mute /unmute /freeze /unfreeze /spec /specoff\n");
        SCM(playerid, COLOR_WHITE, "[ADMIN LVL 1]: /gethere /goto /gethere /clearchat /aduty /(a)dminchat /announce /agotobiz /agotohouse\n" );
        SCM(playerid, COLOR_WHITE, "[ADMIN LVL 2]: /kick /setskin /setvw /setinterior /veh /sethp /ajail /setarmour /rac /arevokedrugs /arevokeguns\n" );
    }
    if(PlayerInfo[playerid][pAdmin] == 3)
    {
  	 	SCM(playerid, COLOR_WHITE, "[ADMIN LVL 1]: /acceptreport /markfalse /warn /mute /unmute /freeze /unfreeze /spec /specoff\n");
        SCM(playerid, COLOR_WHITE, "[ADMIN LVL 1]: /gethere /goto /gethere /clearchat /aduty /(a)dminchat /announce /agotobiz /agotohouse\n" );
        SCM(playerid, COLOR_WHITE, "[ADMIN LVL 2]: /kick /setskin /setvw /veh /sethp /ajail /setarmour /rac /arevokedrugs /arevokeguns\n" );
       	SCM(playerid, COLOR_WHITE, "[ADMIN LVL 3]: /agivegun /givemoney /ban /unbanip /agivedrug /alockbiz /asellbiz /asellhouse /alockhouse /createhouse /deletehouse" );
    }
    if(PlayerInfo[playerid][pAdmin] == 4)
    {
  	 	SCM(playerid, COLOR_WHITE, "[ADMIN LVL 1]: /acceptreport /markfalse /warn /mute /unmute /freeze /unfreeze /spec /specoff\n");
        SCM(playerid, COLOR_WHITE, "[ADMIN LVL 1]: /gethere /goto /gethere /clearchat /aduty /(a)dminchat /announce /agotobiz /agotohouse\n" );
        SCM(playerid, COLOR_WHITE, "[ADMIN LVL 2]: /kick /setskin /setvw /veh /sethp /ajail /setarmour /rac /arevokedrugs /arevokeguns\n" );
       	SCM(playerid, COLOR_WHITE, "[ADMIN LVL 3]: /agivegun /givemoney /ban /unbanip /agivedrug /alockbiz /asellbiz /asellhouse /alockhouse /createhouse /deletehouse" );
    } else return SCM(playerid, COLOR_GREY, "[Error]: You're not authorized to use this command.");
   	return 1;
}

COMMAND:giverespect(playerid, params[])
{
    new
	PID, string[64], Float:X, Float:Y, Float:Z;

    if(sscanf(params, "u", PID)) return SendClientMessage(playerid, COLOR_GREY, "[Usage]: /giverespect [ID].");
    if(!IsPlayerConnected(PID)) return SendClientMessage(playerid, COLOR_LIGHTRED, "[Error]: That player is not connected.");
    if (playerid == PID) return SendClientMessage(playerid, COLOR_LIGHTRED, "[Error]: You can't give yourself respect.");
    if (Respect[playerid] == 1) return SendClientMessage(playerid, COLOR_LIGHTRED,"[Error]: You have to wait until you can give respect again.");
    
    GetPlayerPos(PID, X, Y, Z);
    
    if(IsPlayerInRangeOfPoint(playerid, 5.0, X, Y, Z))
    {
	    PlayerInfo[playerid][pRespect] += 1;
	    SetTimerEx("GiveRespectAgain", 180000, false, "i", playerid);

	    format(string, sizeof(string), "%s gives some respect to %s.", GetName(playerid), GetName(PID));
	    ProxDetector(20.0, playerid, string, COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE);
	}
    return 1;
}

COMMAND:use(playerid, params[])
{
    ShowPlayerDialog(playerid, DIALOG_USE, DIALOG_STYLE_LIST, "Inventory", "Beer\nCigarette\nDrugs\nBoombox", "Use", "Cancel");
    return 1;
}


CMD:agiveboombox(playerid, params[])
{
	new
	targetid, string[64];
	
	if(!IsPlayerAdmin(playerid)) return SCM(playerid, COLOR_GREY, "[Error]: You are not authorized to use this command.");
	if(sscanf(params,"u", targetid)) return SCM(playerid, COLOR_GREY, "[Usage]: /agiveboombox [playerid]");
	PlayerInfo[targetid][pBoombox] = 1;

	format(string, sizeof(string), "AdmCmd: %s has given %s a boombox.", GetName(playerid), GetName(targetid));
	ABroadCast(COLOR_LIGHTRED,string,1);
	
 	format(string, sizeof(string), "AdmCmd: You have been given a boombox by %s.", GetName(playerid));
 	SendClientMessage(targetid, COLOR_LIGHTRED, string);
	return 1;
}

CMD:pay(playerid, params[])
{
    new
	string[64], id, amount;

    if (sscanf(params, "ud", id, amount)) return SendClientMessage(playerid, COLOR_GREY, "[Usage]: /pay [playerid/partname] [amount].");

    if (id == INVALID_PLAYER_ID) return SendClientMessage(playerid, COLOR_LIGHTRED, "[Error]: That player is not connected.");
    if (amount < GetPlayerCash(id)) return SendClientMessage(playerid, COLOR_LIGHTRED, "[Error]: You do not have that amount of money.");
    if (playerid == id) return SendClientMessage(playerid, COLOR_LIGHTRED,"[Error]: You can't give yourself money.");

    GivePlayerCash(id, amount);
    GivePlayerCash(playerid, -amount);
    format(string, sizeof(string), "* You have received $%d from %s.",amount, GetName(playerid));
    SendClientMessage(id, COLOR_GOLD, string);
    format(string, sizeof(string), "%s gives some dollar bills %s.", GetName(playerid), GetName(id));
    ProxDetector(20.0, playerid, string, COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE);

    format(string, sizeof(string), "* You have given %s $%d.",GetName(id),amount);
    SendClientMessage(playerid, COLOR_GOLD, string);
    return 1;
}

CMD:givedrug(playerid, params[])
{
    new
	give[24], id, amount, string[128];
    
    if(sscanf(params, "is[24]d", id, give, amount)) return SendClientMessage(playerid, COLOR_GREY, "[SERVER] /givedrug [playerid] [LSD, Marijuana, Cocaine] [amount]");
    if(!strcmp(give, "lsd", true))
    {
	    if (id == INVALID_PLAYER_ID) return SendClientMessage(playerid, COLOR_LIGHTRED, "[Error]: That player is not connected.");
	    if (amount > PlayerInfo[playerid][dLSD]) return SendClientMessage(playerid, COLOR_LIGHTRED, "[Error]: You do not have that much LSD.");
	    if (playerid == id) return SendClientMessage(playerid, COLOR_LIGHTRED,"[Error]: You can't give yourself LSD.");

	    PlayerInfo[id][dLSD] = amount;
	    PlayerInfo[playerid][dLSD] -= amount;
	    format(string, sizeof(string), "* You have received %dg LSD from %s.",amount, GetName(playerid));
	    SendClientMessage(id, COLOR_GOLD, string);
	    format(string, sizeof(string), "%s gives a baggie to %s.", GetName(playerid), GetName(id));
	    ProxDetector(20.0, playerid, string, COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE);

	    format(string, sizeof(string), "* You have given %s %dg of LSD.",GetName(id),amount);
	    SendClientMessage(playerid, COLOR_GOLD, string);
    }
    else if(!strcmp(give, "marijuana", true))
    {
	    if (id == INVALID_PLAYER_ID) return SendClientMessage(playerid, COLOR_LIGHTRED, "[Error]: That player is not connected.");
	    if (amount > PlayerInfo[playerid][dMarijuana]) return SendClientMessage(playerid, COLOR_LIGHTRED, "[Error]: You do not have that much marijuana.");
	    if (playerid == id) return SendClientMessage(playerid, COLOR_LIGHTRED,"[Error]: You can't give yourself marijuana.");

	    PlayerInfo[id][dMarijuana] = amount;
	    PlayerInfo[playerid][dMarijuana] -= amount;
	    format(string, sizeof(string), "* You have received %dg marijuana from %s.",amount, GetName(playerid));
	    SendClientMessage(id, COLOR_GOLD, string);
	    format(string, sizeof(string), "%s gives a baggie to %s.", GetName(playerid), GetName(id));
	    ProxDetector(20.0, playerid, string, COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE);

	    format(string, sizeof(string), "* You have given %s %dg of marijuana.",GetName(id),amount);
	    SendClientMessage(playerid, COLOR_GOLD, string);
    }
    else if(!strcmp(give, "cocaine", true))
    {
	    if (id == INVALID_PLAYER_ID) return SendClientMessage(playerid, COLOR_LIGHTRED, "[Error]: That player is not connected.");
	    if (amount > PlayerInfo[playerid][dCocaine]) return SendClientMessage(playerid, COLOR_LIGHTRED, "[Error]: You do not have that much cocaine.");
	    if (playerid == id) return SendClientMessage(playerid, COLOR_LIGHTRED,"[Error]: You can't give yourself cocaine.");

	    PlayerInfo[id][dCocaine] = amount;
	    PlayerInfo[playerid][dCocaine] -= amount;
	    format(string, sizeof(string), "* You have received %dg cocaine from %s.",amount, GetName(playerid));
	    SendClientMessage(id, COLOR_GOLD, string);
	    format(string, sizeof(string), "%s gives a baggie to %s.", GetName(playerid), GetName(id));
	    ProxDetector(20.0, playerid, string, COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE);

	    format(string, sizeof(string), "* You have given %s %dg of cocaine.",GetName(id),amount);
	    SendClientMessage(playerid, COLOR_GOLD, string);
    }
    return 1;
}

CMD:knock(playerid, params[])
{
    if(IsPlayerInRangeOfPoint(playerid, 5.0, 1852.2755,-1990.1522,13.5469)) {
    	ShowPlayerDialog(playerid, DIALOG_DRUGSNGUNS, DIALOG_STYLE_LIST, "What you want, holmes?", "Drugs\nWeapons", "Choose", "Cancel"); }
    else if(IsPlayerInRangeOfPoint(playerid, 5.0, 2637.0984,-1991.6788,14.3240)) {
    	ShowPlayerDialog(playerid, DIALOG_DRUGSNGUNS, DIALOG_STYLE_LIST, "What you want, nigga?", "Drugs\nWeapons", "Choose", "Cancel");
    } else return SendClientMessage(playerid, COLOR_LIGHTRED, "[Error]: You need to be at the right door to knock.");
    return 1;
}

CMD:me(playerid, params[])
{
	if(gMuted[playerid]) return SCM(playerid, COLOR_LIGHTRED, "[Error]: You're muted.");
	
    if(isnull(params)) return SendClientMessage(playerid, COLOR_GREY, "[Usage]: /me [text]");
	new string[128];
 	format(string, sizeof(string), "* %s %s", GetName(playerid), params);
 	ProxDetector(20.0, playerid, string, COLOR_PURPLE, COLOR_PURPLE, COLOR_PURPLE, COLOR_PURPLE, COLOR_PURPLE);
    return 1;
}

CMD:do(playerid, params[])
{
	if(gMuted[playerid]) return SCM(playerid, COLOR_LIGHTRED, "[Error]: You're muted.");
	
	if(isnull(params)) return SendClientMessage(playerid, COLOR_GREY, "[Usage]: /do [text]");
	new string[144];
	format(string, sizeof(string), "* %s (( %s ))", params, GetName(playerid));
	ProxDetector(20.0, playerid, string, COLOR_PURPLE, COLOR_PURPLE, COLOR_PURPLE, COLOR_PURPLE, COLOR_PURPLE);
    return 1;
}

CMD:b(playerid, params[])
{
	if(gMuted[playerid]) return SCM(playerid, COLOR_LIGHTRED, "[Error]: You're muted.");
	
    if(isnull(params)) return SendClientMessage(playerid, COLOR_GREY, "[Usage]: /b [text]");
    new string[144];
    format(string, sizeof(string), "(( %s: %s ))", GetName(playerid), params);
    ProxDetector(20.0, playerid, string, COLOR_FADE1,COLOR_FADE2,COLOR_FADE3,COLOR_FADE4,COLOR_FADE5);
    return 1;
}

CMD:ooc(playerid, params[])
{
	if(gMuted[playerid]) return SCM(playerid, COLOR_LIGHTRED, "[Error]: You're muted.");
	if(!OOCenable) return SendClientMessage(playerid, COLOR_LIGHTRED, "[Error]: The OOC chat is currently disabled.");

    if(isnull(params)) return SendClientMessage(playerid, COLOR_GREY, "[Usage]: /(o)oc [text]");
    new string[144];
    
    format(string, sizeof(string), "(( [OOC] %s: %s ))", GetName(playerid), params);
    SendClientMessageToAll(COLOR_OOC,string);
    return 1;
}

CMD:oocstatus(playerid,params[])
{
	new string[128];
    if(PlayerInfo[playerid][pAdmin] < 1) return SCM(playerid,COLOR_GREY,"[Error]: You're not authorized to use this command.");

   	if(!OOCenable)
	{
  		format(string, sizeof(string), "AmdCmd: %s has enabled the OOC chat.", GetName(playerid));
    	SendClientMessageToAll(COLOR_LIGHTRED,string);
		OOCenable = true;
	}
	else if(OOCenable)
	{
  		format(string, sizeof(string), "AmdCmd: %s has disabled the OOC chat.", GetName(playerid));
    	SendClientMessageToAll(COLOR_LIGHTRED,string);
		OOCenable = false;
	}
	return 1;
}


CMD:low(playerid, params[])
{
	if(gMuted[playerid]) return SCM(playerid, COLOR_LIGHTRED, "[Error]: You're muted.");

    if(isnull(params)) return SendClientMessage(playerid, COLOR_GREY, "[Usage]: /(l)ow [text]");
    new string[144];
    format(string, sizeof(string), "%s [LOW]: %s", GetName(playerid), params);
    ProxDetector(8.0, playerid, string, COLOR_GREY, COLOR_FADE1,COLOR_FADE2,COLOR_FADE3,COLOR_FADE4);
    return 1;
}

CMD:help(playerid, params[])
{
	SCM(playerid, COLOR_GOLD, "[Server]: If you need help, please type /helpme and describe your situation.");
    return 1;
}

CMD:shout(playerid, params[])
{
	if(gMuted[playerid]) return SCM(playerid, COLOR_LIGHTRED, "[Error]: You're muted.");
    	
    if(isnull(params)) return SendClientMessage(playerid, COLOR_GREY, "[Usage]: /(s)hout [text]");
	new string[144];
	format(string, sizeof(string), "%s shouts: %s",GetName(playerid), params);
	ProxDetector(50.0, playerid, string, COLOR_FADE1,COLOR_FADE2,COLOR_FADE3,COLOR_FADE4,COLOR_FADE5);
	return 1;
}

CMD:stats(playerid, params[])
{
	new
	string[200], Float:Health;
	GetPlayerHealth(playerid, Health);
	
	format(string, sizeof(string),"_______________________________"COL_WHITE"[%s]"COL_GREEN"_______________________________", GetName(playerid));
	SCM(playerid, COLOR_GREEN, string);
	
	format(string, sizeof(string),"[GENERAL]: Name: %s | Money: $%d | Level: %d | Kills: %d | Respect: %d | Number: %d", GetName(playerid),GetPlayerCash(playerid), PlayerInfo[playerid][pLevel], PlayerInfo[playerid][pKills],PlayerInfo[playerid][pRespect],PlayerInfo[playerid][pNumber]);
	SCM(playerid, COLOR_WHITE, string);
	
	format(string, sizeof(string),"[GENERAL]: Admin Level: %d | Cigarettes: %d | Beers: %d | Business Key: %d | House Key: %d", PlayerInfo[playerid][pAdmin], PlayerInfo[playerid][pCigarettes], PlayerInfo[playerid][pBeer], PlayerInfo[playerid][BizID], PlayerInfo[playerid][HouseID]);
	SCM(playerid, COLOR_WHITE, string);
	
	format(string, sizeof(string),"[GENERAL]: Age: %d | Bank: $%d | Experience: %d", PlayerInfo[playerid][pAge], PlayerInfo[playerid][pBankAccount],  PlayerInfo[playerid][pExperience]);
	SCM(playerid, COLOR_WHITE, string);
	
	format(string, sizeof(string), "[DRUGS]: Marijuana: %d | Cocaine: %d | LSD: %d", PlayerInfo[playerid][dMarijuana], PlayerInfo[playerid][dCocaine], PlayerInfo[playerid][dLSD]);
	SCM(playerid, COLOR_WHITE, string);
	return 1;
}

/*

	[=Police Commands=]

*/



COMMAND:cuff(playerid, params[])
{
    new
	criminal, string[128], Float:X, Float:Y, Float:Z;

    if(sscanf(params, "u", criminal)) return SendClientMessage(playerid, COLOR_GREY, "[Usage]: /cuff [ID].");
    if(criminal == INVALID_PLAYER_ID) return SendClientMessage(playerid, COLOR_LIGHTRED, "[Error]: That player is not connected.");
    if(Duty[playerid] < 1) return SCM(playerid, COLOR_LIGHTRED, "[Error]: You're not a cop on duty.");

    GetPlayerPos(criminal, X, Y, Z);
    if(IsPlayerInRangeOfPoint(playerid, 7.0, X, Y, Z))
	{
	   	SetPlayerSpecialAction(criminal, SPECIAL_ACTION_CUFFED);
	   	SetPlayerAttachedObject(criminal, 9, 19418, 6, -0.011000, 0.028000, -0.022000, -15.600012, -33.699977, -81.700035, 0.891999, 1.000000, 1.168000);
	   	format(string, sizeof(string), "%s cuffs %s.", GetName(playerid), GetName(criminal));
		ProxDetector(15.0, playerid, string, COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE);
	} else return SCM(playerid, COLOR_LIGHTRED, "[Error]: You're not close enough.");
	return 1;
}

COMMAND:uncuff(playerid, params[])
{
    new
	criminal, string[128], Float:X, Float:Y, Float:Z;

    if(sscanf(params, "u", criminal)) return SendClientMessage(playerid, COLOR_GREY, "[Usage]: /cuff [ID].");
    if(criminal == INVALID_PLAYER_ID) return SendClientMessage(playerid, COLOR_LIGHTRED, "[Error]: That player is not connected.");
    if(Duty[playerid] < 1) return SCM(playerid, COLOR_LIGHTRED, "[Error]: You're not a cop on duty.");

    GetPlayerPos(criminal, X, Y, Z);
    if(IsPlayerInRangeOfPoint(playerid, 7.0, X, Y, Z))
	{
	    SetPlayerSpecialAction(criminal, SPECIAL_ACTION_NONE);
	    RemovePlayerAttachedObject(criminal, 9);
	    format(string, sizeof(string), "%s uncuffs %s.", GetName(playerid), GetName(criminal));
	   	ProxDetector(15.0, playerid, string, COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE);
	} else return SCM(playerid, COLOR_LIGHTRED, "[Error]: You're not close enough.");
  	return 1;
}

CMD:megaphone(playerid, params[])
{
	if(gMuted[playerid]) return SCM(playerid, COLOR_LIGHTRED, "[Error]: You're muted.");
	if(Duty[playerid] == 0) return SCM(playerid, COLOR_LIGHTRED, "* You're not on duty.");
    if(isnull(params)) return SendClientMessage(playerid, COLOR_GREY, "[Usage]: /(m)egaphone [text]");
	new string[144];
	format(string, sizeof(string), "[MEGAPGONE] %s: %s",GetName(playerid), params);
	ProxDetector(50.0, playerid, string, COLOR_YELLOW,COLOR_YELLOW,COLOR_YELLOW,COLOR_YELLOW,COLOR_YELLOW);
	return 1;
}

CMD:radio(playerid,params[])
{
	new
	string[128], message[144];
	
    if(Duty[playerid] < 1) return SCM(playerid,COLOR_LIGHTRED,"[Error]: You're not a cop on duty.");
    if(sscanf(params, "s[144]", message)) return SendClientMessage(playerid, COLOR_GREY, "[Usage]: /radio [message]");

	format(string, sizeof(string), "**[CH: LAPD, 993] %s: %s", GetName(playerid), message);
   	PoliceBroadcast(COLOR_LIGHTORANGE,string,1);
	return 1;
}

CMD:duty(playerid,params[])
{
	new string[128];

	if(Duty[playerid] == 0 && IsACop(playerid))
	{
		Duty[playerid] = 1;
		Previous_Colour[playerid] = GetPlayerColor(playerid);
  		format(string, sizeof(string), "LAPD: %s has went on duty.", GetName(playerid));
    	PoliceBroadcast(COLOR_LSPD,string,1);
		SetPlayerColor(playerid, COLOR_LSPD);
	}
	else if(aDuty[playerid] == 1 && IsACop(playerid))
	{
		Duty[playerid] = 1;
		format(string, sizeof(string), "LAPD: %s has went off duty.", GetName(playerid));
    	PoliceBroadcast(COLOR_LSPD,string,1);
		SetPlayerColor(playerid, Previous_Colour[playerid]);
	}
	return 1;
}

COMMAND:arrest(playerid, params[])
{
    new
	criminal, time, string[128];

    if(sscanf(params, "ud", criminal, time)) return SendClientMessage(playerid, COLOR_GREY, "[Usage]: /arrest [ID] [minutes].");
    if(criminal == INVALID_PLAYER_ID) return SendClientMessage(playerid, COLOR_LIGHTRED, "[Error]: That player is not connected.");
    if(Duty[playerid] < 1) return SCM(playerid, COLOR_LIGHTRED, "[Error]: You're not a cop on duty.");

    if(IsPlayerInRangeOfPoint(playerid, 2.0, 1492.0977,-1764.2728,3285.2859))
	{
	    format(string, sizeof(string), "%s pushes %s into the jail cell.", GetName(playerid), GetName(criminal));
	   	ProxDetector(15.0, playerid, string, COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE);
	   	SetPlayerPos(criminal, 1492.2151,-1768.2281,3285.2859);
	   	SetTimerEx("UnJail", 60000*time, false, "i", criminal);
	   	PlayerInfo[criminal][pInJailTime] = time*60000;
	   	PlayerInfo[criminal][pInJail] = 1;
	}
 	else if(IsPlayerInRangeOfPoint(playerid, 2.0, 1495.1206,-1764.4608,3285.2859))
	{
	    format(string, sizeof(string), "%s pushes %s into the jail cell.", GetName(playerid), GetName(criminal));
	   	ProxDetector(15.0, playerid, string, COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE);
	   	SetPlayerPos(criminal, 1495.7794,-1768.0509,3285.2859);
	   	SetTimerEx("UnJail", 60000*time, false, "i", criminal);
	   	PlayerInfo[criminal][pInJailTime] = time*60000;
	   	PlayerInfo[criminal][pInJail] = 1;
	}
 	else if(IsPlayerInRangeOfPoint(playerid, 2.0, 1498.4059,-1764.4614,3285.2859))
	{
	    format(string, sizeof(string), "%s pushes %s into the jail cell.", GetName(playerid), GetName(criminal));
	   	ProxDetector(15.0, playerid, string, COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE);
	   	SetPlayerPos(criminal, 1498.7865,-1768.0172,3285.2859);
	   	SetTimerEx("UnJail", 60000*time, false, "i", criminal);
	   	PlayerInfo[criminal][pInJailTime] = time*60000;
	   	PlayerInfo[criminal][pInJail] = 1;
	}
 	else if(IsPlayerInRangeOfPoint(playerid, 2.0, 1501.6066,-1764.4613,3285.2859))
	{
	    format(string, sizeof(string), "%s pushes %s into the jail cell.", GetName(playerid), GetName(criminal));
	   	ProxDetector(15.0, playerid, string, COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE);
	   	SetPlayerPos(criminal, 1501.7877,-1767.9836,3285.2859);
	   	SetTimerEx("UnJail", 60000*time, false, "i", criminal);
	   	PlayerInfo[criminal][pInJailTime] = time*60000;
	   	PlayerInfo[criminal][pInJail] = 1;
	}
 	else if(IsPlayerInRangeOfPoint(playerid, 2.0, 1501.6797,-1761.9225,3285.2859))
	{
	    format(string, sizeof(string), "%s pushes %s into the jail cell.", GetName(playerid), GetName(criminal));
	   	ProxDetector(15.0, playerid, string, COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE);
	   	SetPlayerPos(criminal, 1501.4619,-1758.5195,3285.2859);
	   	SetTimerEx("UnJail", 60000*time, false, "i", criminal);
	   	PlayerInfo[criminal][pInJailTime] = time*60000;
	   	PlayerInfo[criminal][pInJail] = 1;
	}
 	else if(IsPlayerInRangeOfPoint(playerid, 2.0, 1498.3129,-1761.9176,3285.2859))
	{
	    format(string, sizeof(string), "%s pushes %s into the jail cell.", GetName(playerid), GetName(criminal));
	   	ProxDetector(15.0, playerid, string, COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE);
	   	SetPlayerPos(criminal, 1498.1306,-1758.4500,3285.2859);
	   	SetTimerEx("UnJail", 60000*time, false, "i", criminal);
	   	PlayerInfo[criminal][pInJailTime] = time*60000;
	   	PlayerInfo[criminal][pInJail] = 1;
	}
	else if(IsPlayerInRangeOfPoint(playerid, 2.0, 1495.1941,-1761.9175,3285.2859))
	{
	    format(string, sizeof(string), "%s pushes %s into the jail cell.", GetName(playerid), GetName(criminal));
	   	ProxDetector(15.0, playerid, string, COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE);
	   	SetPlayerPos(criminal, 1494.9525,-1758.6340,3285.2859);
	   	SetTimerEx("UnJail", 60000*time, false, "i", criminal);
	   	PlayerInfo[criminal][pInJailTime] = time*60000;
	   	PlayerInfo[criminal][pInJail] = 1;
	}
	else if(IsPlayerInRangeOfPoint(playerid, 2.0, 1491.9694,-1761.9091,3285.2859))
	{
	    format(string, sizeof(string), "%s pushes %s into the jail cell.", GetName(playerid), GetName(criminal));
	   	ProxDetector(15.0, playerid, string, COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE);
	   	SetPlayerPos(criminal, 1491.8241,-1758.4966,3285.2859);
	   	SetTimerEx("UnJail", 60000*time, false, "i", criminal);
	   	PlayerInfo[criminal][pInJailTime] = time*60000;
	   	PlayerInfo[criminal][pInJail] = 1;
	}
	else return SCM(playerid, COLOR_LIGHTRED, "[Error]: You're not at the arrest point.");
  	return 1;
}


COMMAND:locker(playerid, params[])
{
	if(Duty[playerid] < 1) return SCM(playerid, COLOR_LIGHTRED, "[Error]: You're not a cop on duty.");
 	if(IsPlayerInRangeOfPoint(playerid, 3.0, 1456.4370,-1761.2609,3285.2859))
	{
		ShowPlayerDialog(playerid, DIALOG_LOCKER, DIALOG_STYLE_LIST, "LAPD Locker", "Armour\nNightstick\nPepper-Spray\nDeagle\nShotgun\nMP5\nM4", "Choose", "Cancel");
	} else return SCM(playerid, COLOR_LIGHTRED, "[Error]: You're not by the LAPD locker.");
	return 1;
}

/*

	[=Administrator Commands=]

*/


CMD:givemoney(playerid, params[])
{
    new
	id, cash, string[128];
	
    if(PlayerInfo[playerid][pAdmin] < 3) return SCM(playerid, COLOR_GREY, "[Error]: You're not authorized to use that command.");
    if(sscanf(params,"ui", id, cash)) return SCM(playerid, COLOR_GREY,"[Usage]: /givemoney [playerid/partofname] [amount].");
    if(!IsPlayerConnected(id)) return SCM(playerid, COLOR_LIGHTRED,"[Error]: That player is not connected.");
    
	GivePlayerCash(id, cash);

	format(string,sizeof(string),"AdmCmd: %s has given %s $%d.", GetName(playerid), GetName(id), cash);
	ABroadCast(COLOR_LIGHTRED,string,1);
	format(string,sizeof(string),"AdmCmd: You have received $%d from administrator %s.", cash, GetName(playerid));
	SendClientMessage(id, COLOR_LIGHTRED, string);
    return 1;
}

CMD:setweather(playerid, params[])
{
	if(PlayerInfo[playerid][pAdmin] < 1) return SCM(playerid, COLOR_LIGHTRED, "You can't do this.");
    if ( isnull ( params ) ) return SendClientMessage( playerid, -1, #Usage: /setweather [ID]. );
    SetWeather( strval ( params ) );
    return true;
}

CMD:warn(playerid, params[])
{
    new
	id, reason[124], string[124], plrIP[16];
	
    if(PlayerInfo[playerid][pAdmin] < 1) return SCM(playerid, COLOR_GREY, "[Error]: You're not authorized to use that command.");
    if(sscanf(params,"us[100]",id,reason)) return SCM(playerid, COLOR_GREY,"[Usage]: /warn [playerid/partofname] [reason].");
    if(!IsPlayerConnected(id)) return SCM(playerid, COLOR_LIGHTRED,"[Error]: That player is not connected.");
    if(Warns[playerid] >= 5)
	{
		format(string, sizeof(string), "AdmCmd: %s was banned by %s. Reason: 5 warnings.", GetName(playerid), GetName(id));
		SendClientMessageToAll(COLOR_LIGHTRED, string);
		GetPlayerIp(id,plrIP, sizeof(plrIP));
		SendClientMessage(id,COLOR_LIGHTRED,"|___________[BAN INFO]___________|");
		format(string, sizeof(string), "Your name: %s.",GetName(id));
		SendClientMessage(id, COLOR_LIGHTRED, string);
		format(string, sizeof(string), "Your IP: %s.",plrIP);
		SendClientMessage(id, COLOR_LIGHTRED, string);
		format(string, sizeof(string), "Banned by: %s.",GetName(playerid));
		SendClientMessage(id, COLOR_LIGHTRED, string);
		SendClientMessage(id,COLOR_LIGHTRED,"Reason: 5 warnings.");
		SendClientMessage(id,COLOR_LIGHTRED,"|___________[BAN INFO]___________|");
		SetTimerEx("UnsetBan", 500, 0, "i", id);
        }
	Warns[playerid] += 1;

	format(string, sizeof(string), "AdmCmd: %s was warned by %s, reason: %s", GetName(id), GetName(playerid), reason);
	SendClientMessageToAll(COLOR_LIGHTRED,string);
	return 1;
}

CMD:ban(playerid, params[])
{
	if(PlayerInfo[playerid][pAdmin] >= 3)
	{
 		new
 		PID, reason[64], str[128], plrIP[16];
   	 	
     	if(sscanf(params, "us[100]", PID,reason)) return SendClientMessage(playerid, COLOR_GREY, "[Usage]: /ban [playerid] [reason]");

		if(!IsPlayerConnected(PID))
		return SendClientMessage(playerid, COLOR_GREY, "[Error]: That player is not connected.");

		format(str, sizeof(str), "AdmCmd: %s has been banned by administrator %s. Reason: %s ", GetName(PID), GetName(playerid), reason);
        SendClientMessageToAll(COLOR_LIGHTRED, str);
        
        GetPlayerIp(playerid, plrIP, sizeof(plrIP));
        
        SendClientMessage(PID,COLOR_LIGHTRED,"|___________[BAN INFO]___________|");
        format(str, sizeof(str), "Your name: %s.",GetName(PID));
        SendClientMessage(PID, COLOR_LIGHTRED, str);
        format(str, sizeof(str), "Your ip is: %s.", plrIP);
        SendClientMessage(PID, COLOR_LIGHTRED, str);
        format(str, sizeof(str), "You were banned by: %s.",GetName(playerid));
        SendClientMessage(PID, COLOR_LIGHTRED, str);
        format(str, sizeof(str), "You were banned for: %s.",reason);
        SendClientMessage(PID, COLOR_LIGHTRED, str);
        SendClientMessage(PID,COLOR_LIGHTRED,"|___________[BAN INFO]___________|");
        SetTimerEx("UnsetBan", 500, 0, "i", PID);
		PlayerInfo[PID][pBanned] = 1;

	}
		else
  	{
   		SendClientMessage(playerid, COLOR_GREY, "[Error]: You're not authorized to use that command.");
	}
	return 1;
}

CMD:unbanip(playerid,params[])
{
    new
	ip[32], dformat[64];
	
    if(PlayerInfo[playerid][pAdmin] < 3) return SCM(playerid,COLOR_GREY,"[Error]: You're not authorized to use this command.");
    if(sscanf(params,"s[32]",ip)) return SCM(playerid,COLOR_GREY,"[Usage]: /unbanip [IP]");
    format(dformat,sizeof dformat,"unbanip %s",ip);
    SendRconCommand(dformat);
    return 1;
}

CMD:offlineban(playerid, params[])
{
    new targetname[24], filestring[79];
    if(sscanf(params, "s[24]", targetname)) return SendClientMessage(playerid, COLOR_GREY, "[Usage]: /offlineban [playerName]");
    format(filestring, sizeof(filestring), "/Users/%s.ini", targetname);
    if(!fexist(filestring)) return SendClientMessage(playerid, COLOR_LIGHTRED, "[Error]: That player does not exist.");
    else
    {
        new INI:File = INI_Open(filestring);
        INI_SetTag(File, "data");
        INI_WriteInt(File, "Banned", 1);
        INI_Close(File);
        new done[128];
        format(done, sizeof(done), "* You have successfully banned player %s.", targetname);
        SendClientMessage(playerid, COLOR_LIGHTRED, done);
    }
    return 1;
}

CMD:unban(playerid, params[])
{
    new tname[24];
    if(sscanf(params, "s[24]", tname)) return SendClientMessage(playerid,-1,"Correct Usage: /unban [playerName] ");
    new filestring[79];
    format(filestring, sizeof(filestring), "/Users/%s.ini", tname);
    if(!fexist(filestring)) return SendClientMessage(playerid, COLOR_LIGHTRED, "[Error]: That player does not exist.");
    else
    {
        new INI:File = INI_Open(filestring);
        INI_SetTag(File, "data");
        INI_WriteInt(File, "Banned",0);
        INI_Close(File);
        INI_ParseFile(filestring, "LoadIP_%s", .bExtra = true , .extra = playerid);
        new cmdstring[44];
        format(cmdstring, sizeof(cmdstring), "unbanip %s", PlayerInfo[playerid][BannedIP]);
        SendRconCommand(cmdstring);
        SendRconCommand("reloadbans");
        new done[128];
        format(done, sizeof(done),"* You have successfully unbanned %s.", tname);
        SendClientMessage(playerid, COLOR_LIGHTRED,done);
    }
    return 1;
}

CMD:bank(playerid,params[])
{
	SetPlayerPos(playerid, 2690.8713,-610.8880,-71.6582);
    return 1;
}

CMD:adminduty(playerid,params[])
{
	new string[128];
	
    if(PlayerInfo[playerid][pAdmin] < 1) return SCM(playerid,COLOR_GREY,"[Error]: You're not authorized to use this command.");
   	if(aDuty[playerid] == 0)
	{
		aDuty[playerid] = 1;
		Previous_Colour[playerid] = GetPlayerColor(playerid);
  		format(string, sizeof(string), "AmdCmd: %s has went on adminduty.", GetName(playerid));
    	ABroadCast(COLOR_LIGHTRED,string,1);
		SetPlayerColor(playerid, COLOR_ADMIN);
	}
	else if(aDuty[playerid] == 1)
	{
		aDuty[playerid] = 0;
		format(string, sizeof(string), "AmdCmd: %s has went off adminduty.", GetName(playerid));
    	ABroadCast(COLOR_LIGHTRED,string,1);
		SetPlayerColor(playerid, Previous_Colour[playerid]);
	}
	return 1;
}

COMMAND:ajail(playerid, params[])
{
    new
	criminal, time, string[128];

    if(PlayerInfo[playerid][pAdmin] < 2) return SCM(playerid,COLOR_GREY,"[Error]: You're not authorized to use this command.");
    if(sscanf(params, "ud", criminal, time)) return SendClientMessage(playerid, COLOR_GREY, "[Usage]: /ajail [ID] [minutes].");
    if(criminal == INVALID_PLAYER_ID) return SendClientMessage(playerid, COLOR_LIGHTRED, "[Error]: That player is not connected.");
    
   	format(string, sizeof(string), "AdmCmd: %s has been adminjailed by %s for %d minutes.", GetName(criminal), GetName(playerid), time);
 	SendClientMessageToAll(COLOR_LIGHTRED,string);
    
   	SetPlayerPos(criminal, 2525.1736,-1673.8074,14.8601);
   	SetTimerEx("UnJail", 60000*time, false, "i", criminal);
   	return 1;
}

CMD:setskin(playerid, params[])
{
    new
	id, skin, string[128];
	
    if(PlayerInfo[playerid][pAdmin] < 2) return SCM(playerid,COLOR_GREY,"[Error]: You're not authorized to use this command.");
    else if(sscanf(params,"ui", id, skin)) return SCM(playerid, COLOR_GREY,"[Usage]: /setskin [playerid/partofname] [skinID].");
    else if(skin > 299 || skin < 1) return SCM(playerid, COLOR_LIGHTRED,"[Error]: Invalid skin ID.  [0-299].");
    else if(!IsPlayerConnected(id)) return SCM(playerid, COLOR_LIGHTRED,"That player is not connected.");
    
    format(string, sizeof(string),"AdmCmd: Your skin has been changed by %s.", GetName(playerid));
    SendClientMessage(id, COLOR_LIGHTRED, string);
    SetPlayerSkin(id, skin);
    
    PlayerInfo[playerid][pSkin] = skin;
    return 1;
}

COMMAND:freeze(playerid,params[])
{
    if(PlayerInfo[playerid][pAdmin] >= 1)
    {
    	new
		Target, astring[128];
   		
    	if(sscanf(params, "u", Target)) SendClientMessage(playerid, COLOR_GREY, "[Usage]: /freeze [playerid]");
    	if(!IsPlayerConnected(Target))
    	return SendClientMessage(playerid, COLOR_LIGHTRED, "[Error]: That player is not connected.");
    	
    	if(!sscanf(params, "u", Target))
     	{
      		if(PlayerInfo[Target][pAdmin] > PlayerInfo[playerid][pAdmin]) return SendClientMessage(playerid,COLOR_LIGHTRED,"[Error]: You can't perform this action on adminstrators with a higher level than you.");
      		
   			format(astring,sizeof(astring),"AmdCmd: Administrator %s has frozen %s.",GetName(playerid),GetName(Target));
   			SendClientMessageToAll(COLOR_LIGHTRED,astring);
		   	TogglePlayerControllable(Target,0);
            }
    }
    else return SendClientMessage(playerid,COLOR_GREY,"[Error]: You're not authorized to use this command.");
    return 1;
}

COMMAND:unfreeze(playerid,params[])
{
    if(PlayerInfo[playerid][pAdmin] >= 1)
    {
		new
		Target, astring[128];
   		
     	if(sscanf(params, "u", Target)) SendClientMessage(playerid, COLOR_GREY, "[Usage]: /unfreeze [playerid]");
     	if(!IsPlayerConnected(Target))
     	return SendClientMessage(playerid, COLOR_LIGHTRED, "[Error]: That player is not connected.");
     	
     	if(!sscanf(params, "u", Target))
      	{
       		if(PlayerInfo[Target][pAdmin] > PlayerInfo[playerid][pAdmin]) return SendClientMessage(playerid,COLOR_LIGHTRED,"ERROR: You cant perform this on Admins that are higher than your level!");

       		format(astring,sizeof(astring),"AmdCmd: Administrator %s has unfrozen %s.",GetName(playerid),GetName(Target));
       		SendClientMessageToAll(COLOR_LIGHTRED,astring);
       		TogglePlayerControllable(Target,1);
            }
	}
    else return SendClientMessage(playerid,COLOR_GREY,"[Error]: You're not authorized to use this command.");
    return 1;
}

CMD:makeadmin(playerid, params[])
{
    new
	pID, value, string[124];
	
    if(PlayerInfo[playerid][pAdmin] < 4 && !IsPlayerAdmin(playerid)) return SCM( playerid, COLOR_GREY, "[Error]: You're not authorized to use this command.");
    else if (sscanf(params, "ui", pID, value)) return SCM(playerid, COLOR_GREY, "[Usage]: /makeadmin [playerid/partofname] [level 1-4].");
    else if (value < 0 || value > 4) return SCM(playerid, COLOR_LIGHTRED, "[Error]: Invalid administrator level, 0-4.");
    else if(!IsPlayerConnected(pID)) return SCM(playerid, COLOR_LIGHTRED, "[Error]: That player is not connected.");

 	format(string, sizeof(string), "AdmCmd: %s has set %s's admin-level to %d.", GetName(playerid), GetName(pID), value);
 	SendClientMessageToAll(COLOR_LIGHTRED,string);
	PlayerInfo[pID][pAdmin] = value;
    return 1;
}

CMD:gethere(playerid,params[])
{
    new
	ID, Float:x, Float:y, Float:z;
    
    if(PlayerInfo[playerid][pAdmin] < 1) return SCM( playerid, COLOR_GREY, "[Error]: You're not authorized to use this command.");
    else if(sscanf(params, "u", ID)) return SCM(playerid, COLOR_GREY, "[Usage]: /gethere [playerid/partofname].");
    else if(!IsPlayerConnected(ID)) return SCM(playerid, COLOR_LIGHTRED, "[Error]: That player is not connected.");
    
    GetPlayerPos(playerid, x, y, z);
    SetPlayerPos(ID, x, y+0.5, z+0.5);
    SetPlayerInterior(ID, GetPlayerInterior(playerid));
    return 1;
}

CMD:goto(playerid, params[])
{
    new
	ID, Float:x, Float:y, Float:z;
    
    if(PlayerInfo[playerid][pAdmin] < 1) return SCM( playerid, COLOR_GREY, "[Error]: You're not authorized to use this command.");
    else if(sscanf(params, "u", ID)) return SCM(playerid, COLOR_GREY, "[Usage]: /goto [partofname/playerid].");
    else if(!IsPlayerConnected(ID)) return SCM(playerid, COLOR_LIGHTRED, "[Error]: That player is not connected.");

	GetPlayerPos(ID, x, y, z);
	SetPlayerPos(playerid, x+1, y+1, z);
    SetPlayerInterior(playerid, GetPlayerInterior(ID));
    return 1;
}

CMD:spraytag(playerid, params[])
{
	new
	Float:x, Float:y, Float:z, Float:a;

	if(gTeam[playerid] == BALLAS)
	{
		GetPlayerFacingAngle(playerid, a);
		GetPlayerPos(playerid, x, y, z);
		Spray[playerid] = CreateDynamicObject(1490, x, y, z + 0.2, 0.0, 0.0, a + 90);
		ApplyAnimation(playerid, "SPRAYCAN", "spraycan_full", 4.0, 0, 1, 1, 1, 1, 1);
	}
	else if(gTeam[playerid] == GROVE)
	{
		GetPlayerFacingAngle(playerid, a);
		GetPlayerPos(playerid, x, y, z);
		Spray[playerid] = CreateDynamicObject(18659, x, y, z + 0.2, 0.0, 0.0, a + 90);
		ApplyAnimation(playerid, "SPRAYCAN", "spraycan_full", 4.0, 0, 1, 1, 1, 1, 1);
 	}
	else if(gTeam[playerid] == SEVILLE)
	{
		GetPlayerFacingAngle(playerid, a);
		GetPlayerPos(playerid, x, y, z);
		Spray[playerid] = CreateDynamicObject(1528, x, y, z + 0.2, 0.0, 0.0, a + 90);
		ApplyAnimation(playerid, "SPRAYCAN", "spraycan_full", 4.0, 0, 1, 1, 1, 1, 1);
	}
	else if(gTeam[playerid] == VAGOS)
	{
		GetPlayerFacingAngle(playerid, a);
		GetPlayerPos(playerid, x, y, z);
		Spray[playerid] = CreateDynamicObject(1530, x, y, z + 0.2, 0.0, 0.0, a + 90);
		ApplyAnimation(playerid, "SPRAYCAN", "spraycan_full", 4.0, 0, 1, 1, 1, 1, 1);
	}
	else if(gTeam[playerid] == AZTECAS)
	{
		GetPlayerFacingAngle(playerid, a);
		GetPlayerPos(playerid, x, y, z);
		Spray[playerid] = CreateDynamicObject(1531, x, y, z + 0.2, 0.0, 0.0, a + 90);
		ApplyAnimation(playerid, "SPRAYCAN", "spraycan_full", 4.0, 0, 1, 1, 1, 1, 1);
	}
    return 1;
}


CMD:arevokeguns(playerid, params[])
{
	new id;
	if( PlayerInfo[ playerid ][ pAdmin ] < 2 ) return SCM( playerid, COLOR_GREY, "[Error]: You're not authorized to use this command.");
    if(sscanf(params,"u", id)) return SCM(playerid, COLOR_GREY,"[Usage]: /revokeguns [playerid/partofname].");
    RemoveWeapons(id);
	return 1;
}

CMD:arevokedrugs(playerid, params[])
{
	new id;
	if( PlayerInfo[ playerid ][ pAdmin ] < 2 ) return SCM( playerid, COLOR_GREY, "[Error]: You're not authorized to use this command.");
    if(sscanf(params,"u", id)) return SCM(playerid, COLOR_GREY,"[Usage]: /revokedrugs [playerid/partofname].");
    RemoveDrugs(id);
	return 1;
}

CMD:kick(playerid, params[])
{
		new
		PID, reason[64], str[128];
            
  		if( PlayerInfo[ playerid ][ pAdmin ] < 2 ) return SCM( playerid, COLOR_GREY, "[Error]: You're not authorized to use this command.");
		if(sscanf(params, "us[64]", PID,reason)) return SendClientMessage(playerid, COLOR_GREY, "[Usage]: /kick [playerid] [reason]"); //tell sscanf if the parameters/the syntax is written wrong to return a message (PID and the reason used here)

		if(!IsPlayerConnected(PID)) return SendClientMessage(playerid, COLOR_LIGHTRED, "[Error]: That player is not connected!");

		format(str, sizeof(str), "AdmCmd: %s has been kicked by administrator %s. Reason: %s ", GetName(PID), GetName(playerid), reason); //format the string we've defined to send the message, playername and adminname are used to receive the information about the names
		SendClientMessageToAll(COLOR_LIGHTRED, str); //send that message to all
		SetTimerEx("UnsetKick", 500, 0, "i", PID);
		return 1;
	}

CMD:adminchat(playerid, params[])
{
	new
	string[144], text[144];
	if( PlayerInfo[ playerid ][ pAdmin ] < 1 ) return SCM( playerid, COLOR_GREY, "[Error]: You're not authorized to use this command.");
	if (sscanf(params, "s[144]", text)) return SCM(playerid, COLOR_GREY, "[Usage]: /(a)dminchat [message]");
	
	format(string, sizeof(string), "[Admin Chat] %s: %s", GetName(playerid), text);
 	ABroadCast(COLOR_ADMIN, string, 1);
	return 1;
}

CMD:announcement(playerid, params[])
{
	new
	string[144], text[144];
	if( PlayerInfo[ playerid ][ pAdmin ] < 1 ) return SCM( playerid, COLOR_GREY, "[Error]: You're not authorized to use this command.");
	if (sscanf(params, "s[144]", text)) return SCM(playerid, COLOR_GREY, "[Usage]: /announcement [message]");
	
	format(string, sizeof(string), "[Admin Announcement] %s: %s", GetName(playerid), text);
 	SendClientMessageToAll(COLOR_ADMIN, string);
	return 1;
}


CMD:veh(playerid, params[]) {

	new
	vehid, Float:x, Float:y, Float:z;

	if( PlayerInfo[ playerid ][ pAdmin ] < 2 ) return SCM( playerid, COLOR_GREY, "[Error]: You're not authorized to use this command.");
	if(sscanf(params, "i", vehid)) SendClientMessage(playerid, COLOR_GREY, "[Usage]: /veh [veh]");
	if (vehid < 400 || vehid > 611) SendClientMessage(playerid, COLOR_LIGHTRED, "[Error]: Invalid vehicle ID. [400-611]");

	GetPlayerPos(playerid, x, y, z);
	vCar[playerid] = CreateVehicle(vehid, x + 3, y, z, 0, 0,0, -1);
	SendClientMessage(playerid, COLOR_LIGHTRED, "AdmCmd: The vehicle has been spawned.");
	return 1;
}

COMMAND:clearchat( playerid, params[ ] )
{
	new
	astring[124];

    if( PlayerInfo[ playerid ][ pAdmin ] < 1 ) return SCM( playerid, COLOR_GREY, "[Error]: You're not authorized to use this command.");
    {
        for( new i = 0; i <= 100; i ++ ) SendClientMessageToAll( COLOR_WHITE, "" );
       	format(astring,sizeof(astring),"AmdCmd: Administrator %s has cleared the chat.", GetName(playerid));
		SendClientMessageToAll(COLOR_LIGHTRED,astring);
    }
    return 1;
}

COMMAND:respawnvehicles(playerid,params[])
{
	new
	astring[124];

    if( PlayerInfo[ playerid ][ pAdmin ] < 2 ) return SCM( playerid, COLOR_GREY, "[Error]: You're not authorized to use this command.");
    {
		for(new i=0;i<MAX_VEHICLES;i++)
  		{
    		if(IsVehicleOccupied(i) == 0)
      		{
        		SetVehicleToRespawn(i);
          	}
        }
  		format(astring,sizeof(astring),"AmdCmd: Administrator %s has respawned all empty public vehicles.", GetName(playerid));
		SendClientMessageToAll(COLOR_LIGHTRED,astring);
    }
    return 1;
}

COMMAND:spec(playerid, params[])
{
    new
	id;
	
    if( PlayerInfo[ playerid ][ pAdmin ] < 1 ) return SendClientMessage( playerid, COLOR_GREY, "[Error]: You're not authorized to use this command." );
    if(sscanf(params,"u", id))return SendClientMessage(playerid, COLOR_GREY, "Usage: /spec [id]");
    if(id == playerid)return SendClientMessage(playerid,COLOR_LIGHTRED,"[Error]: You cannot spectate yourself.");
    if(id == INVALID_PLAYER_ID)return SendClientMessage(playerid, COLOR_LIGHTRED, "[Error]: That player is not connected.");
    GetPlayerPos(playerid,SpecX[playerid],SpecY[playerid],SpecZ[playerid]);
    Inter[playerid] = GetPlayerInterior(playerid);
    vWorld[playerid] = GetPlayerVirtualWorld(playerid);
    TogglePlayerSpectating(playerid, true);
    if(IsPlayerInAnyVehicle(id))
    {
        if(GetPlayerInterior(id) > 0)
        {
            SetPlayerInterior(playerid,GetPlayerInterior(id));
        }
        if(GetPlayerVirtualWorld(id) > 0)
        {
            SetPlayerVirtualWorld(playerid,GetPlayerVirtualWorld(id));
        }
        PlayerSpectateVehicle(playerid,GetPlayerVehicleID(id));
    }
    else
    {
        if(GetPlayerInterior(id) > 0)
        {
            SetPlayerInterior(playerid,GetPlayerInterior(id));
        }
        if(GetPlayerVirtualWorld(id) > 0)
        {
            SetPlayerVirtualWorld(playerid,GetPlayerVirtualWorld(id));
        }
        PlayerSpectatePlayer(playerid,id);
    }
    GetPlayerName(id, Name, sizeof(Name));
    format(String, sizeof(String),"AmdCmd: You're currently spectating %s.",Name);
    SendClientMessage(playerid,COLOR_LIGHTRED,String);
    IsSpecing[playerid] = 1;
    IsBeingSpeced[id] = 1;
    spectatorid[playerid] = id;
    return 1;
}

COMMAND:specoff(playerid, params[])
{
    if( PlayerInfo[ playerid ][ pAdmin ] < 1 ) return SendClientMessage( playerid, COLOR_GREY, "[Error]: You're not authorized to use this command." );
    if(IsSpecing[playerid] == 0)return SendClientMessage(playerid,COLOR_LIGHTRED,"[Error]: You are not spectating anyone.");
    TogglePlayerSpectating(playerid, 0);
    return 1;
}

CMD:mute(playerid, params[])
{
	new
	Target, astring[128];
	
	
 	if( PlayerInfo[ playerid ][ pAdmin ] < 1 ) return SendClientMessage( playerid, COLOR_GREY, "[Error]: You're not authorized to use this command." );
 	if(sscanf(params,"u", Target))return SendClientMessage(playerid, COLOR_GREY, "Usage: /mute [id]");
 	
    gMuted[playerid] = 1;
   	format(astring,sizeof(astring),"AmdCmd: Administrator %s has muted %s.", GetName(playerid), GetName(Target));
	SendClientMessageToAll(COLOR_LIGHTRED,astring);
    return true;
}

CMD:unmute(playerid, params[])
{
	new
	Target, astring[128];


 	if( PlayerInfo[ playerid ][ pAdmin ] < 1 ) return SendClientMessage( playerid, COLOR_GREY, "[Error]: You're not authorized to use this command." );
 	if(sscanf(params, "u", Target)) SendClientMessage(playerid, COLOR_GREY, "[Usage]: /unmute [playerid]");
	
	format(astring,sizeof(astring),"AmdCmd: Administrator %s has unmuted %s.", GetName(playerid), GetName(Target));
	SendClientMessageToAll(COLOR_LIGHTRED,astring);
	gMuted[playerid] = 0;
    return true;
}

CMD:report(playerid,params[])
{
    new
	id, reason[144], string[124], name[MAX_PLAYERS], name2[MAX_PLAYERS];
	
    if(sscanf(params,"us[100]", id, reason)) return SCM(playerid, COLOR_GREY,"[Usage]: /report [playerid/partofname] [reason].");
    if(!IsPlayerConnected(id)) return SCM(playerid, COLOR_LIGHTRED,"[Error]: That player is not connected.");
    
    GetPlayerName(playerid, name, sizeof(name));
    GetPlayerName(id, name2, sizeof(name2));
    format(string, sizeof(string), "[ID:%d] %s has reported [ID:%d]%s, reason: %s.", playerid, GetName(playerid), id, GetName(id), reason);
    ABroadCast(COLOR_LIGHTRED,string,1);
    
    format(string, sizeof(string), "AmdCmd: Type /markfalse [id] or /acceptreport [id].");
    ABroadCast(COLOR_LIGHTRED,string,1);
    format(string, sizeof(string), "* Your report was sent to all the online Adminstrators.");
    SendClientMessage(playerid,COLOR_GREEN,string);
    PlayerNeedsHelp[playerid] = 1;
    return 1;
}

CMD:helpme(playerid,params[])
{
    new
	id, reason[144], string[124], name[MAX_PLAYERS], name2[MAX_PLAYERS];
	
    if(sscanf(params,"s[100]", reason)) return SCM(playerid, COLOR_GREY,"[Usage]: /helpme [message].");

    GetPlayerName(playerid, name, sizeof(name));
    GetPlayerName(id, name2, sizeof(name2));
    format(string, sizeof(string), "[ID:%d] %s has asked for help: %s", playerid, GetName(playerid), reason);
    ABroadCast(COLOR_LIGHTRED,string,1);

    format(string, sizeof(string), "* Your message was sent to all of the online Administrators.");
    SendClientMessage(playerid,COLOR_GREEN,string);
    return 1;
}

CMD:acceptreport(playerid, params[])
{
    new
	id, string[124], name[MAX_PLAYERS];
	
    if(PlayerInfo[playerid][pAdmin] < 1) return SCM(playerid, COLOR_GREY,"[Error]: You're not authorized to use this command.");
    if(sscanf(params,"u", id)) return SCM(playerid, COLOR_GREY,"[Usage]: /acceptreport [playerid]");
    if(!IsPlayerConnected(id)) return SCM(playerid, COLOR_LIGHTRED,"That player is not connected.");
    else {
        if(PlayerNeedsHelp[id] == 1) {
            PlayerNeedsHelp[id] = 0;
            GetPlayerName(id, name, sizeof(name));
            format(string, sizeof(string), "AdmCmd: %s has accepted the report by %s [ID:%d].", GetName(playerid), GetName(id), id);
            ABroadCast(COLOR_LIGHTRED, string, 1);
            format(string, sizeof(string), "AdmCmd: %s has accepted your report. You will now receive help, be patient.", GetName(playerid));
            SendClientMessage(id, COLOR_LIGHTRED, string);
        }
        else return SCM(playerid, COLOR_LIGHTRED,"[Error]: That players has not made a report.");
    }
    return 1;
}


CMD:markfalse(playerid, params[])
{
    new
	id, string[124];
    
    if(PlayerInfo[playerid][pAdmin] < 1) return SCM(playerid, COLOR_GREY,"[Error]: You're not authorized to use this command.");
    if(sscanf(params,"u", id)) return SCM(playerid, COLOR_GREY,"[Usage]: /markfalse [playerid].");
    if(!IsPlayerConnected(id)) return SCM(playerid, COLOR_LIGHTRED,"That player is not connected.");
    else {
        if(PlayerNeedsHelp[id] == 1) {
            PlayerNeedsHelp[id] = 0;

            format(string, sizeof(string), "AdmCmd: %s has ignored the report by [ID:%d]%s.", GetName(playerid), id, GetName(id));
            ABroadCast(COLOR_LIGHTRED, string, 1);
            format(string, sizeof(string), "*AdmCmd: %s has ignored your report for a reason, write a proper report next time.", GetName(playerid));
            SendClientMessage(id, COLOR_LIGHTRED, string);
        }
        else return SCM(playerid, COLOR_LIGHTRED,"[Error]: That players has not made a report.");
    }
    return 1;
}

CMD:setvw(playerid,params[])
{
	new
	id, world, string[124];
	
    if(PlayerInfo[playerid][pAdmin] < 1) return SCM(playerid, COLOR_GREY,"[Error]: You're not authorized to use this command.");
    if(sscanf(params,"ui", id, world)) return SCM(playerid, COLOR_GREY,"[Usage]: /setvw [playerid/partofname] [world id].");
    if(!IsPlayerConnected(id)) return SCM(playerid, COLOR_LIGHTRED,"That player is not connected.");

	format(string, sizeof(string), "AmdCmd: %s has set your virtual world to %d.",GetName(playerid), world);
	SendClientMessage(playerid, COLOR_LIGHTRED, string);
	SetPlayerVirtualWorld(id, world);
    return 1;
}

CMD:setinterior(playerid,params[])
{
	new
	id, interior, string[124];

    if(PlayerInfo[playerid][pAdmin] < 1) return SCM(playerid, COLOR_GREY,"[Error]: You're not authorized to use this command.");
    if(sscanf(params,"ui", id, interior)) return SCM(playerid, COLOR_GREY,"[Usage]: /setinterior [playerid/partofname] [interior id].");
    if(!IsPlayerConnected(id)) return SCM(playerid, COLOR_LIGHTRED,"That player is not connected.");

	format(string, sizeof(string), "AmdCmd: %s has set your interior id to %d.",GetName(playerid), interior);
	SendClientMessage(playerid, COLOR_LIGHTRED, string);
	SetPlayerInterior(id, interior);
    return 1;
}


CMD:sethp(playerid, params[])
{
    new
	id, hp, string[128];
    
    if(PlayerInfo[playerid][pAdmin] < 2) return SCM(playerid, COLOR_GREY,"[Error]: You're not authorized to use this command.");
    else if(sscanf(params,"ui", id, hp)) return SCM(playerid, COLOR_GREY,"[Usage]: /sethp [playerid/partofname] [hp].");
    else if(hp > 90 || hp < 1) return SCM(playerid, COLOR_LIGHTRED,"[Error]: Amount [1-90].");
    if(!IsPlayerConnected(id)) return SCM(playerid, COLOR_LIGHTRED,"That player is not connected.");
    
    SetPlayerHealth(id, hp);
    format(string, sizeof(string), "AdmCmd: %s has set %s's HP to %d.", GetName(playerid), GetName(id), hp);
    SendClientMessageToAll(COLOR_LIGHTRED,string);
    return 1;
}

CMD:setarmour(playerid, params[])
{
    new
	id, armour, string[128];

    if(PlayerInfo[playerid][pAdmin] < 2) return SCM(playerid, COLOR_GREY,"[Error]: You're not authorized to use this command.");
    else if(sscanf(params,"ui", id, armour)) return SCM(playerid, COLOR_GREY,"[Usage]: /setarmour [playerid/partofname] [armour].");
    else if(armour > 90 || armour < 1) return SCM(playerid, COLOR_LIGHTRED,"[Error]: Amount [1-90].");
    if(!IsPlayerConnected(id)) return SCM(playerid, COLOR_LIGHTRED,"That player is not connected.");

    SetPlayerArmour(id, armour);
    format(string, sizeof(string), "AdmCmd: %s has set %s's HP to %d.", GetName(playerid), GetName(id), armour);
    SendClientMessageToAll(COLOR_LIGHTRED,string);
    return 1;
}

CMD:agivegun(playerid, params[])
{
    new
	id, gunname[32], string[124], weapon, ammo;
    
    if(PlayerInfo[playerid][pAdmin] < 3) return SCM(playerid, COLOR_GREY,"[Error]: You're not authorized to use this command.");
    else if(sscanf(params,"uii", id, weapon, ammo)) return SCM(playerid, COLOR_GREY,"[Usage]: /agivegun [playerid/partofname] [gunid] [ammo].");
    else if(weapon > 47 || weapon < 1) return SCM(playerid, COLOR_LIGHTRED,"[Error]: Weapon ID'S: [1-47].");
    else if(ammo > 999 || ammo < 1) return SCM(playerid, COLOR_LIGHTRED,"[Error]: Ammo [1-999].");

	GivePlayerWeapon(id, weapon, ammo);
	GetWeaponName(weapon, gunname,sizeof(gunname));
 	format(string, sizeof(string), "AdmCmd: %s has given %s %s.", GetName(playerid), GetName(id), gunname);
    SendClientMessageToAll(COLOR_LIGHTRED,string);
    return 1;
}

CMD:createbiz(playerid, params[])
{
	new
	price, level, id, int, world, string[128], Float:Xi,
	Float:Yi, Float:Zi, inti, Float:X,Float:Y,Float:Z,Float:A;
	new biztext[144];
    if(PlayerInfo[playerid][pAdmin] < 4) return SCM(playerid, COLOR_GREY,"[Error]: You're not authorized to use this command.");
    if(sscanf(params, "dddfff", price, level, inti, Xi, Yi, Zi)) return SendClientMessage(playerid, COLOR_GREY, "[Usage]: /createbiz [price] [type] [interior] [X] [Y] [Z]");

    if(level < 0 || level > 20) return SendClientMessage(playerid, COLOR_LIGHTRED, "[Error]: Type cannot go below 0, or above 20.");//

    if(price < 10000) return SendClientMessage(playerid, COLOR_LIGHTRED, "[Error]: Price cannot go below $10,000.");

    for(new h = 1;h < sizeof(BusinessInfo);h++)
    {
        if(BusinessInfo[h][bPrice] == 0)
        {
            id = h;
            break;
        }
    }
    
    GetPlayerPos(playerid, X, Y, Z);
    GetPlayerFacingAngle(playerid, A);
    int = GetPlayerInterior(playerid);
    world = GetPlayerVirtualWorld(playerid);
    BusinessInfo[id][bInsideInt] = inti;
    BusinessInfo[id][bExitX] = Xi;
    BusinessInfo[id][bExitY] = Yi;
    BusinessInfo[id][bExitZ] = Zi;

    BusinessInfo[id][bOwned] = 0;
    BusinessInfo[id][bPrice] = price;
    BusinessInfo[id][bType] = level;
    BusinessInfo[id][bEntranceX] = X;
    BusinessInfo[id][bEntranceY] = Y;
    BusinessInfo[id][bEntranceZ] = Z;
    BusinessInfo[id][bEntranceA] = A;
    BusinessInfo[id][bLocked] = 1;

   	switch(BusinessInfo[id][bType])
    {
 			case 20: biztext = "Dealership";
 			case 19: biztext = "Electronic Store";
   			case 18: biztext = "Ammunition";
   			case 17: biztext = "Gym";
   			case 16: biztext = "Hotel";
   			case 15: biztext = "Motel";
   			case 14: biztext = "Diner";
         	case 13: biztext = "Tattoo Store";
         	case 12: biztext = "Barbershop";
            case 11: biztext = "Flower Store";
           	case 10: biztext = "98 Cents";
    		case 9: biztext = "69 Cents";
            case 8: biztext = "Liqour Store";
	    	case 7: biztext = "Restaurant";
	    	case 6: biztext = "Bank";
	    	case 5: biztext = "Hospital";
	        case 4: biztext = "Police Station";
	        case 3: biztext = "24/7";
	        case 2: biztext = "Club";
	        case 1: biztext = "Bar";
	        case 0: biztext = "Clothes Shop";
    }

   	format(string,sizeof(string),""COL_BROWN"Owner: "COL_WHITE"None\n"COL_BROWN"Price: "COL_WHITE"$%d\n"COL_BROWN"Type: "COL_WHITE"%s\n"COL_BROWN"Street Number: "COL_WHITE"%d", BusinessInfo[id][bPrice], biztext, id);
	BusinessInfo[id][DLabel] = Create3DTextLabel(string, 0xFFFFFF, X, Y, Z, 10.0, 0, 0);

    BusinessInfo[id][bInt] =int;
    BusinessInfo[id][bWorld] =world;
    BusinessInfo[id][bInsideWorld] =id;
    OnPlayerUpdate(playerid);

    format(string, sizeof(string), "None");
    strmid(BusinessInfo[id][bName], string, 0, strlen(string), 255);

    if(BusinessInfo[id][bOutsideIcon]) DestroyDynamicPickup(BusinessInfo[id][bOutsideIcon]);
    BusinessInfo[id][bOutsideIcon] = CreateDynamicPickup(1239, 1, BusinessInfo[id][bEntranceX], BusinessInfo[id][bEntranceY], BusinessInfo[id][bEntranceZ], BusinessInfo[id][bWorld]);
    new file4[40];
    format(file4, sizeof(file4), BPATH, id);
    new INI:File = INI_Open(file4);
    INI_SetTag(File,"data");
    INI_WriteInt(File,"bOwned", BusinessInfo[id][bOwned]);
    INI_WriteInt(File,"bPrice", BusinessInfo[id][bPrice]);
    INI_WriteString(File,"bOwner", BusinessInfo[id][bOwner]);
    INI_WriteInt(File,"bType", BusinessInfo[id][bType]);
    INI_WriteInt(File,"bLocked", BusinessInfo[id][bLocked]);
    INI_WriteInt(File,"bMoney", BusinessInfo[id][bMoney]);
    INI_WriteFloat(File,"bEntranceX", BusinessInfo[id][bEntranceX]);
    INI_WriteFloat(File,"bEntranceY", BusinessInfo[id][bEntranceY]);
    INI_WriteFloat(File,"bEntranceZ", BusinessInfo[id][bEntranceZ]);
    INI_WriteFloat(File,"bEntranceA", BusinessInfo[id][bEntranceA]);
    INI_WriteFloat(File,"bExitX", BusinessInfo[id][bExitX]);
    INI_WriteFloat(File,"bExitY", BusinessInfo[id][bExitY]);
    INI_WriteFloat(File,"bExitZ", BusinessInfo[id][bExitZ]);
    INI_WriteFloat(File,"bExitA", BusinessInfo[id][bExitA]);
    INI_WriteInt(File,"bInt", BusinessInfo[id][bInt]);
    INI_WriteInt(File,"bWorld", BusinessInfo[id][bWorld]);
    INI_WriteInt(File,"bInsideInt", BusinessInfo[id][bInsideInt]);
    INI_WriteInt(File,"bInsideWorld", BusinessInfo[id][bInsideWorld]);
    INI_WriteString(File,"bName", BusinessInfo[id][bName]);
    INI_Close(File);
    return 1;
}

CMD:deletebiz(playerid, params[])
{
    new
	id = IsPlayerNearBizEnt(playerid);
 	if(PlayerInfo[playerid][pAdmin] < 3) return SCM(playerid, COLOR_GREY,"[Error]: You're not authorized to use this command.");
 	if(BusinessInfo[id][bOwned] == 1) return SCM(playerid, COLOR_LIGHTRED, "* This business is owned.");//Checks if the biz is owned, if it is it won't allow it to be deleted.
 	
    BusinessInfo[id][bOwned] = 0;
    BusinessInfo[id][bPrice] = 0;
    BusinessInfo[id][bOwner] = 0;
    BusinessInfo[id][bType] = 0;
    BusinessInfo[id][bLocked] = 0;
    BusinessInfo[id][bName] = 0;
    BusinessInfo[id][bMoney] = 0;
    BusinessInfo[id][bEntranceX] = 0;
    BusinessInfo[id][bEntranceY] = 0;
    BusinessInfo[id][bEntranceZ] = 0;
    BusinessInfo[id][bEntranceA] = 0;
    BusinessInfo[id][bExitX] = 0;
    BusinessInfo[id][bExitY] = 0;
    BusinessInfo[id][bExitZ] = 0;
    BusinessInfo[id][bExitA] = 0;
    BusinessInfo[id][bInt] = 0;
    BusinessInfo[id][bWorld] = 0;
    
    Delete3DTextLabel(BusinessInfo[id][DLabel]);

	DestroyDynamicPickup(BusinessInfo[id][bOutsideIcon]);
    
    OnPlayerUpdate(playerid);

    new string[128];

    format(string, sizeof(string), BPATH, id);
    fremove(string);
    return 1;
}

CMD:agivedrug(playerid, params[])
{
    new
	give[24], id, amount, string[128];

    if(sscanf(params, "is[24]d", id, give, amount)) return SendClientMessage(playerid, COLOR_GREY, "[SERVER] /agivedrug [playerid] [LSD, Marijuana, Cocaine] [amount]");
    if(PlayerInfo[playerid][pAdmin] < 3) return SCM(playerid, COLOR_GREY,"[Error]: You're not authorized to use this command.");
    if(!strcmp(give, "lsd", true))
    {
	    if (id == INVALID_PLAYER_ID) return SendClientMessage(playerid, COLOR_LIGHTRED, "[Error]: That player is not connected.");

	    PlayerInfo[id][dLSD] = amount;
	 	format(string, sizeof(string), "AdmCmd: %s has given %s %d grams of LSD.", GetName(playerid), GetName(id), amount);
	    ABroadCast(COLOR_LIGHTRED,string,1);
    }
    else if(!strcmp(give, "marijuana", true))
    {
	    if (id == INVALID_PLAYER_ID) return SendClientMessage(playerid, COLOR_LIGHTRED, "[Error]: That player is not connected.");

	    PlayerInfo[id][dMarijuana] = amount;
	 	format(string, sizeof(string), "AdmCmd: %s has given %s %d grams of marijuana.", GetName(playerid), GetName(id), amount);
	    ABroadCast(COLOR_LIGHTRED,string,1);
    }
    else if(!strcmp(give, "cocaine", true))
    {
	    if (id == INVALID_PLAYER_ID) return SendClientMessage(playerid, COLOR_LIGHTRED, "[Error]: That player is not connected.");

	    PlayerInfo[id][dCocaine] = amount;
	 	format(string, sizeof(string), "AdmCmd: %s has given %s %d grams of cocaine.", GetName(playerid), GetName(id), amount);
	    ABroadCast(COLOR_LIGHTRED,string,1);
    }
    return 1;
}

CMD:opencell(playerid, params[])
{
	if(IsACop(playerid))
	{
	    if(IsPlayerInRangeOfPoint(playerid, 2.0,1491.21484375,-1764.90002441,3284.25048828)) //Cell0
		{
		    MoveDynamicObject(cell0,1491.21484375-1.25,-1764.90002441,3284.25048828,0.50);
		    PlayerActionMessage(playerid, 20.0, "inserts the keys and opens the cell.");
		}
		else if(IsPlayerInRangeOfPoint(playerid, 2.0,1494.41210938,-1764.90002441,3284.25048828)) //Cell1
		{
		    MoveDynamicObject(cell1,1494.41210938-1.25,-1764.90002441,3284.25048828,0.50);
		    PlayerActionMessage(playerid, 20.0, "inserts the keys and opens the cell.");
		}
		else if(IsPlayerInRangeOfPoint(playerid, 2.0,1497.61132812,-1764.90002441,3284.25048828)) //Cell2
		{
		    MoveDynamicObject(cell2,1497.61132812-1.25,-1764.90002441,3284.25048828,0.50);
		    PlayerActionMessage(playerid, 20.0, "inserts the keys and opens the cell.");
		}
		else if(IsPlayerInRangeOfPoint(playerid, 2.0,1500.81445312,-1764.90002441,3284.25048828)) //Cell3
		{
		    MoveDynamicObject(cell3,1500.81445312-1.25,-1764.90002441,3284.25048828,0.50);
		    PlayerActionMessage(playerid, 20.0, "inserts the keys and opens the cell.");
		}
		else if(IsPlayerInRangeOfPoint(playerid, 2.0,1500.81994629,-1761.51000977,3284.25048828)) //Cell4
		{
		    MoveDynamicObject(cell4,1500.81994629-1.25,-1761.51000977,3284.25048828,0.50);
		    PlayerActionMessage(playerid, 20.0, "inserts the keys and opens the cell.");
		}
		else if(IsPlayerInRangeOfPoint(playerid, 2.0,1491.22094727,-1761.50000000,3284.25048828)) //Cell5
		{
		    MoveDynamicObject(cell5,1491.22094727-1.25,-1761.50000000,3284.25048828,0.50);
		    PlayerActionMessage(playerid, 20.0, "inserts the keys and opens the cell.");
		}
		else if(IsPlayerInRangeOfPoint(playerid, 2.0,1494.41894531,-1761.51000977,3284.25048828)) //Cell6
		{
		    MoveDynamicObject(cell6,1494.41894531-1.25,-1761.51000977,3284.25048828,0.50);
		    PlayerActionMessage(playerid, 20.0, "inserts the keys and opens the cell.");
		}
		else if(IsPlayerInRangeOfPoint(playerid, 2.0,1497.61999512,-1761.51000977,3284.25048828)) //Cell7
		{
		    MoveDynamicObject(cell7,1497.61999512-1.25,-1761.51000977,3284.25048828,0.50);
		    PlayerActionMessage(playerid, 20.0, "inserts the keys and opens the cell.");
		}	else return SCM(playerid, COLOR_LIGHTRED, "[Error]: You're not by any cell.");
	} else return SCM(playerid, COLOR_LIGHTRED, "[Error]: You're not a cop.");
	return 1;
}

CMD:prison(playerid, params[])
{

	SetPlayerPos(playerid, 1480.5524,-1777.0132,3281.7954);
	return 1;
}

CMD:closecell(playerid, params[])
{
	if(IsACop(playerid))
	{
	    if(IsPlayerInRangeOfPoint(playerid, 2.0,1491.21484375,-1764.90002441,3284.25048828)) //Cell0
		{
		    MoveDynamicObject(cell0,1491.21484375,-1764.90002441,3284.25048828,0.50);
		    PlayerActionMessage(playerid, 20.0, "inserts the keys and closes the cell.");
		}
		else if(IsPlayerInRangeOfPoint(playerid, 2.0,1494.41210938,-1764.90002441,3284.25048828)) //Cell1
		{
		    MoveDynamicObject(cell1,1494.41210938,-1764.90002441,3284.25048828,0.50);
		    PlayerActionMessage(playerid, 20.0, "inserts the keys and closes the cell.");
		}
		else if(IsPlayerInRangeOfPoint(playerid, 2.0,1497.61132812,-1764.90002441,3284.25048828)) //Cell2
		{
		    MoveDynamicObject(cell2,1497.61132812,-1764.90002441,3284.25048828,0.50);
		    PlayerActionMessage(playerid, 20.0, "inserts the keys and closes the cell.");
		}
		else if(IsPlayerInRangeOfPoint(playerid, 2.0,1500.81445312,-1764.90002441,3284.25048828)) //Cell3
		{
		    MoveDynamicObject(cell3,1500.81445312,-1764.90002441,3284.25048828,0.50);
		    PlayerActionMessage(playerid, 20.0, "inserts the keys and closes the cell.");
		}
		else if(IsPlayerInRangeOfPoint(playerid, 2.0,1500.81994629,-1761.51000977,3284.25048828)) //Cell4
		{
		    MoveDynamicObject(cell4,1500.81994629,-1761.51000977,3284.25048828,0.50);
		    PlayerActionMessage(playerid, 20.0, "inserts the keys and closes the cell.");
		}
		else if(IsPlayerInRangeOfPoint(playerid, 2.0,1491.22094727,-1761.50000000,3284.25048828)) //Cell5
		{
		    MoveDynamicObject(cell5,1491.22094727,-1761.50000000,3284.25048828,0.50);
		    PlayerActionMessage(playerid, 20.0, "inserts the keys and closes the cell.");
		}
		else if(IsPlayerInRangeOfPoint(playerid, 2.0,1494.41894531,-1761.51000977,3284.25048828)) //Cell6
		{
		    MoveDynamicObject(cell6,1494.41894531,-1761.51000977,3284.25048828,0.50);
		    PlayerActionMessage(playerid, 20.0, "inserts the keys and closes the cell.");
		}
		else if(IsPlayerInRangeOfPoint(playerid, 2.0,1497.61999512,-1761.51000977,3284.25048828)) //Cell7
		{
		    MoveDynamicObject(cell7,1497.61999512,-1761.51000977,3284.25048828,0.50);
		    PlayerActionMessage(playerid, 20.0, "inserts the keys and closes the cell.");
		}	else return SCM(playerid, COLOR_LIGHTRED, "[Error]: You're not by any cell.");
	} else return SCM(playerid, COLOR_LIGHTRED, "[Error]: You're not a cop.");
	return 1;
}

CMD:opendoor(playerid, params[])
{
	if(IsACop(playerid))
	{
		if(IsPlayerInRangeOfPoint(playerid, 2.0,1487.00000000,-1762.42504883,3284.23608398) && IsACop(playerid)) //Door 0
		{
		    MoveDynamicObject(door0, 1487.00000000,-1762.42504883+1.25,3284.23608398, 0.50);
		    PlayerActionMessage(playerid, 20.0, "unlocks and opens the door.");

		}
		else if(IsPlayerInRangeOfPoint(playerid, 2.0, 1483.79003906,-1762.42504883,3284.23608398) && IsACop(playerid)) //Door 1
		{
		    MoveDynamicObject(door1,1483.79003906,-1762.42504883+1.25,3284.23608398,0.50);
		    PlayerActionMessage(playerid, 20.0, "unlocks and opens the door.");

		}
		else if(IsPlayerInRangeOfPoint(playerid, 2.0, 1479.85998535,-1758.31994629,3284.23388672) && IsACop(playerid)) //Door 2
		{
		    MoveDynamicObject(door2,1479.85998535-1.25,-1758.31994629,3284.23388672,0.50);
		    PlayerActionMessage(playerid, 20.0, "unlocks and opens the door.");

		}
		else if(IsPlayerInRangeOfPoint(playerid, 2.0, 1467.06701660,-1758.31994629,3284.23388672) && IsACop(playerid)) //Door 3
		{
		    MoveDynamicObject(door3,1467.06701660-1.25,-1758.31994629,3284.23388672,0.50);
		    PlayerActionMessage(playerid, 20.0, "unlocks and opens the door.");
		} else return SCM(playerid, COLOR_LIGHTRED, "[Error]: You're not by any door.");
	} else return SCM(playerid, COLOR_LIGHTRED, "[Error]: You're not a cop.");
	return 1;
}

CMD:closedoor(playerid, params[])
{
	if(IsACop(playerid))
	{
		if(IsPlayerInRangeOfPoint(playerid, 2.0,1487.00000000,-1762.42504883,3284.23608398)) //Door 0
		{
		    MoveDynamicObject(door0,1487.00000000,-1762.42504883,3284.23608398,0.50);
		    PlayerActionMessage(playerid, 20.0, "closes the door and locks it.");

		}
	 	else if(IsPlayerInRangeOfPoint(playerid, 2.0, 1483.79003906,-1762.42504883,3284.23608398)) //Door 1
		{
		    MoveDynamicObject(door1,1483.79003906,-1762.42504883,3284.23608398,0.50);
		    PlayerActionMessage(playerid, 20.0, "closes the door and locks it.");

		}
		else if(IsPlayerInRangeOfPoint(playerid, 2.0, 1479.85998535,-1758.31994629,3284.23388672)) //Door 2
		{
		    MoveDynamicObject(door2,1479.85998535,-1758.31994629,3284.23388672,0.50);
		    PlayerActionMessage(playerid, 20.0, "closes the door and locks it.");

		}
		else if(IsPlayerInRangeOfPoint(playerid, 2.0, 1467.06701660,-1758.31994629,3284.23388672)) //Door 3
		{
		    MoveDynamicObject(door3,1467.06701660,-1758.31994629,3284.23388672,0.50);
		    PlayerActionMessage(playerid, 20.0, "closes the door and locks it.");
		} else return SCM(playerid, COLOR_LIGHTRED, "[Error]: You're not by any door.");
	} else return SCM(playerid, COLOR_LIGHTRED, "[Error]: You're not a cop.");
	return 1;
}
    	
CMD:licenses(playerid, params[])
{
	new licensetext[18];
	new gendertext[18];
	switch(PlayerInfo[playerid][pDriverLicense])
	{
		case 1: licensetext = "Yes";
		case 0: licensetext = "No";
	}

	switch(PlayerInfo[playerid][pGender])
	{
		case 1: gendertext = "Female";
		case 0: gendertext = "Male";
	}

 	new
	PID, string[128];

    if(sscanf(params, "us[144]", PID)) return SCM(playerid, COLOR_GREY, "[Usage]: /licenses  [PlayerID]");
    if(!IsPlayerConnected(PID)) return SCM(playerid, COLOR_LIGHTRED, "[Error]: That player is not connected.");


	format(string, sizeof(string),"________"COL_WHITE"[%s]"COL_GREEN"________", GetName(playerid));
	SCM(PID, COLOR_GREEN, string);
	format(string, sizeof(string),"Age: %d", PlayerInfo[playerid][pAge]);
	SCM(PID, COLOR_WHITE, string);
	format(string, sizeof(string),"Gender: %d", gendertext);
	SCM(PID, COLOR_WHITE, string);
	format(string, sizeof(string),"Drivers License: %s.", licensetext);
	SCM(PID, COLOR_WHITE, string);
	return 1;
}

CMD:advertise(playerid, params[])
{
	new
	string[144], text[144];
	if(!IsPlayerInRangeOfPoint(playerid, 10.0, 1684.4441, -1343.2681, 17.4371)) return SCM(playerid, COLOR_LIGHTRED, "[Error]: You're not at the advertisement center.");
	if(AdvertiseAllowed[playerid] != 0) return SCM(playerid, COLOR_LIGHTRED, "[Error]: You have to wait one minute before posting an advertisement again.");
	if (sscanf(params, "s[144]", text)) return SCM(playerid, COLOR_GREY, "[Usage]: /(ad)vertisement [message]");
	
	format(string, sizeof(string), "Advertisement: %s, Number: %d", text, PlayerInfo[playerid][pNumber]);
	SendClientMessageToAll(COLOR_ADVERTISEMENT, string);
	SetTimerEx("AdvertiseAgain", 60000, false, "i", playerid);
	AdvertiseAllowed[playerid] = 1;
	return 1;
}

CMD:acceptdeath(playerid, params[])
{
	if(isAlive[playerid] == false)
	{
	    SCM(playerid, COLOR_LIGHTRED, "* You have been rushed to the hospital and are undergoing an operation.");
	    SetPlayerPos(playerid, -211.3207,-1759.6207,676.7153);
	    SetPlayerInterior(playerid, 3);
		FadeColorForPlayer(playerid,0,0,0,0,0,0,0,255,15,0);
     	SetTimerEx("OperationDone", 15000, false, "i", playerid);
     	isAlive[playerid] = true;
  		ApplyAnimation(playerid,"CRACK","crckdeth1",4.1,1,1,1,1,1,1);
		ResetWeapons(playerid);
	}
	return 1;
}


CMD:takedrivingtest(playerid, params[])
{
	if(PlayerInfo[playerid][pAge] < 16) return SCM(playerid, COLOR_LIGHTRED, "[Error]: You're not old enough to take the test.");
    if(!IsPlayerInRangeOfPoint(playerid, 10.0, 2045.0376, -1913.1846, 13.5469)) return SCM(playerid, COLOR_LIGHTRED, "[Error]: You're not at the DMV center.");
    if(TakingDriverLicense[playerid] == true) return SCM(playerid, COLOR_LIGHTRED, "[Error]: You're already taking the test.");
    if(PlayerInfo[playerid][pDriverLicense] == 1) return SCM(playerid, COLOR_LIGHTRED, "[Error]: You already have a drivers license.");
    
    TakingDriverLicense[playerid] = true;
	SCM(playerid, COLOR_GOLD, "* Please enter one of the white DMV cars to start the test.");
	return 1;
}

CMD:engine(playerid,params[])
{
	new string[124];
	new id = GetVehicleID(GetPlayerVehicleID(playerid));
 	new vehicleid = GetPlayerVehicleID(playerid);
	if(GetPlayerVehicleAccess(playerid, id) < 1)
		return SendClientMessage(playerid, COLOR_RED, "* You don't have the keys for this vehicle!");
    GetVehicleParamsEx(vehicleid, engine, lights, alarm, doors, bonnet, boot, objective);
    if(GetPlayerState(playerid) == 2)
    {
		if(engine != 1)
		{
			SetVehicleParamsEx(vehicleid, 1, 1, alarm, doors, bonnet, boot, 0);
	  		format(string, sizeof(string), "* %s turns the engine on.", GetName(playerid));
	  		ProxDetector(20.0, playerid, string, COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE);
		}
		else if(engine != 0)
		{
			SetVehicleParamsEx(vehicleid, 0, 0, alarm, doors, bonnet, boot, 0);
			format(string, sizeof(string), "* %s turns the engine off.", GetName(playerid));
	  		ProxDetector(20.0, playerid, string, COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE);
		}
	}
	return 1;
}

CMD:lights(playerid,params[])
{
	new string[124];
	new vehicleid = GetPlayerVehicleID(playerid);

    GetVehicleParamsEx(vehicleid, engine, lights, alarm, doors, bonnet, boot, objective);
    if(GetPlayerState(playerid) == 2)
    {
		if(lights != 1)
		{
			SetVehicleParamsEx(vehicleid, engine, 1, alarm, doors, bonnet, boot, 0);
	  		format(string, sizeof(string), "* %s turns the lights on.", GetName(playerid));
	  		ProxDetector(20.0, playerid, string, COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE);
		}
		else if(lights != 0)
		{
			SetVehicleParamsEx(vehicleid, engine, 0, alarm, doors, bonnet, boot, 0);
			format(string, sizeof(string), "* %s turns the lights off.", GetName(playerid));
	  		ProxDetector(20.0, playerid, string, COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE,COLOR_PURPLE);
		}
	}
	return 1;
}

CMD:s(playerid, params[]) return cmd_shout(playerid, params);
CMD:acmds(playerid, params[]) return cmd_admincommands(playerid, params);
CMD:acommands(playerid, params[]) return cmd_admincommands(playerid, params);
CMD:ahelp(playerid, params[]) return cmd_admincommands(playerid, params);
CMD:o(playerid, params[]) return cmd_ooc(playerid, params);
CMD:r(playerid, params[]) return cmd_radio(playerid, params);
CMD:l(playerid, params[]) return cmd_low(playerid, params);
CMD:aduty(playerid, params[]) return cmd_adminduty(playerid, params);
CMD:p(playerid, params[]) return cmd_pickup(playerid, params);
CMD:h(playerid, params[]) return cmd_hangup(playerid, params);
CMD:ad(playerid, params[]) return cmd_advertise(playerid, params);
CMD:a(playerid, params[]) return cmd_adminchat(playerid, params);
CMD:m(playerid, params[]) return cmd_megaphone(playerid, params);

public OnPlayerDeath(playerid, killerid, reason)
{
    PlayerInfo[killerid][pKills]++;
    PlayerInfo[playerid][pDeaths]++;
    
    SetPlayerSkin(playerid, PlayerInfo[playerid][pSkin]);
    SetPlayerColor(playerid, COLOR_WHITE);
    TogglePlayerControllable(playerid, 1);
    TextDrawHideForPlayer(playerid,txtTimeDisp);
    
    GetPlayerPos(playerid, Deadx[playerid], Deady[playerid], Deadz[playerid]);
    
   	isAlive[playerid] = false;

    if(IsBeingSpeced[playerid] == 1)//If the player being spectated, dies, then turn off the spec mode for the spectator.
    {
        foreach(Player,i)
        {
            if(spectatorid[i] == playerid)
            {
                TogglePlayerSpectating(i,false);// This justifies what's above, if it's not off then you'll be either spectating your connect screen, or somewhere in blueberry (I don't know why)
            }
        }
    }
    return 1;
}

public OnPlayerText(playerid, text[])
{
	if(gMuted[playerid]) return SCM(playerid, COLOR_LIGHTRED, "[Error]: You're muted.");
	
	if(oncall[playerid] == 1)
	{
    	for(new i = 0; i <= MAX_PLAYERS; i++)
     	{
      		if(IsPlayerConnected(i) == 1)
        	{
         		if(Mobile[i] == playerid)
           		{
             	new string[126];
              	format(string, sizeof(string), "%s says (cellphone): %s", GetName(playerid), text);
              	ProxDetector(20.0, playerid, string,COLOR_FADE1,COLOR_FADE2,COLOR_FADE3,COLOR_FADE4,COLOR_FADE5);
              	format(string, sizeof(string), "%s says (cellphone): %s", GetName(playerid), text);
              	SendClientMessage(i,  COLOR_YELLOW, string);
              	return 0;
               	}
			}
		}
	}
	if(IsPlayerInAnyVehicle(playerid))
	{
 		ApplyAnimation(playerid, "CAR_CHAT", "CAR_Sc3_FL", 4.1, 0, 1, 1, 1, 1, 1);
		new string[144];
		format(string, sizeof(string), "%s says: %s",GetName(playerid), text);
		ProxDetector(20.0, playerid, string, COLOR_FADE1,COLOR_FADE2,COLOR_FADE3,COLOR_FADE4,COLOR_FADE5);
   		return 0;
 	}
	if(MaskOn[playerid] == 1)
	{
		new string[126];

		format(string, sizeof(string), "Stranger_%d%d says: %s", playerid, masknumber[playerid], text);
		ProxDetector(20.0, playerid, string, COLOR_FADE1,COLOR_FADE2,COLOR_FADE3,COLOR_FADE4,COLOR_FADE5);
		return 0;
	}

	new string[144];
	format(string, sizeof(string), "%s says: %s",GetName(playerid), text);
	ProxDetector(20.0, playerid, string, COLOR_FADE1,COLOR_FADE2,COLOR_FADE3,COLOR_FADE4,COLOR_FADE5);
	return 0;
}

public OnPlayerConnect(playerid)
{
//RASH
        pLogged[playerid] = 0;
        PlayerInfo[playerid][pSex] = 0;
        PlayerInfo[playerid][pSkin] = 200;
        PlayerInfo[playerid][pMoney] = 2500;
        PlayerInfo[playerid][pLevel] = 1;
        GetPlayerName(playerid,PlayerInfo[playerid][pName],24);
        format(qwery,256,"SELECT * FROM `playerinfo` WHERE `name` = '%s' LIMIT 1",PlayerInfo[playerid][pName]);
        mysql_query(qwery);
        mysql_store_result();
        if(!mysql_fetch_row_format(qwery))
        {
			ShowPlayerDialog(playerid,1,1,"Регистрация на \"Pawn-Wiki.Ru\"","Здравствуйте,добро пожаловать на \"Pawn-Wiki.Ru\"!\nЧто-бы начать играть вам нужно:\n1.Зарегестрироваться;\n2.Заполнить анкету;\n3.Пройти обучение.\nЧто-бы зарегестрироваться,\nпожалуйте введите пароль ниже!\n\t\tPawn-Wiki.Ru","Далее","");
        }
        else
        {
			ShowPlayerDialog(playerid,4,0,"Последние новости","Новости сервера:","Далее","");
        }
//RASH
	FadePlayerConnect(playerid);
	SetPlayerColor(playerid, COLOR_WHITE);
    ResetPlayerStats(playerid);
    stopanimAllowed[playerid] = true;
    gettime(hour, minute);
    SetPlayerTime(playerid,hour,minute);
    
   	RemoveBuildingForPlayer(playerid, 617, 1178.6016, -1332.0703, 12.8906, 0.25);
	RemoveBuildingForPlayer(playerid, 618, 1177.7344, -1315.6641, 13.2969, 0.25);
	RemoveBuildingForPlayer(playerid, 620, 1541.4531, -1709.6406, 13.0469, 0.25);
	RemoveBuildingForPlayer(playerid, 620, 1541.4531, -1642.0313, 13.0469, 0.25);
	RemoveBuildingForPlayer(playerid, 1287, 1725.1797, -1270.5938, 13.1250, 0.25);
	RemoveBuildingForPlayer(playerid, 1288, 1725.1797, -1269.6641, 13.1250, 0.25);
	RemoveBuildingForPlayer(playerid, 1289, 1725.1797, -1268.8984, 13.1250, 0.25);
	RemoveBuildingForPlayer(playerid, 1285, 1725.1797, -1272.5781, 13.1250, 0.25);
	RemoveBuildingForPlayer(playerid, 1286, 1725.1797, -1271.5625, 13.1250, 0.25);
	RemoveBuildingForPlayer(playerid, 1308, 2071.9844, -1922.1250, 11.6016, 0.25);
	RemoveBuildingForPlayer(playerid, 5231, 2085.2813, -1909.7109, 23.0000, 0.25);
	RemoveBuildingForPlayer(playerid, 1283, 1930.3750, -1753.1016, 15.5938, 0.25);
	RemoveBuildingForPlayer(playerid, 1308, 2091.1641, -1826.8359, 12.7031, 0.25);
	RemoveBuildingForPlayer(playerid, 1308, 2128.3125, -1826.8359, 12.7031, 0.25);
	RemoveBuildingForPlayer(playerid, 1307, 2295.7031, -1742.1953, 12.7500, 0.25);
    new Hospital = CreatePlayerObject(playerid, 19353, -195.4142, -1741.4693, 676.4188, 0.0000, 0.0000, 180);
	SetPlayerObjectMaterialText(playerid, Hospital, "HOSPITAL", 0, 140, "Cambria", 130, 1, -1, 0, 1);

	new SAC = CreateDynamicObject(19353, -195.4142, -1741.4362, 676.8190, 0.0000, 0.0000, 180);
	SetObjectMaterialText(SAC, "SAN ANDREAS COUNTY", 0, 140, "Cambria", 55, 1, -584707328, 0, 1);

	new line1 = CreateDynamicObject(19353, -195.4142, -1739.7816, 676.8000, 0.0000, 0.0000, 180);
	SetObjectMaterialText(line1, "|", 0, 140, "Arial", 200, 1, -13750738, 0, 1);

	new line2 = CreateDynamicObject(19353, -195.4142, -1743.1800, 676.8000, 0.0000, 0.0000, 180);
	SetObjectMaterialText(line2, "|", 0, 140, "Arial", 200, 1, -13750738, 0, 1);

    new name[MAX_PLAYER_NAME];
    GetPlayerName(playerid, name, sizeof(name));
    if (!IsRPName(name))
    {
        SendClientMessage(playerid, COLOR_LIGHTRED, "You have been kicked for using a NON-RP name, please use a name with a Firstname_Lastname format.");
        UnsetKick(playerid);
    }
    return 1;
}

public OnPlayerDisconnect(playerid, reason)
{
    new INI:File = INI_Open(UserPath(playerid));
    INI_SetTag(File,"data");

 	FadePlayerDisconnect(playerid);
	TextDrawDestroy(SpeedoText[playerid]);
	new
	pskin = GetPlayerSkin(playerid);
	
	PlayerInfo[playerid][pSkin] = pskin;

    GetPlayerPos(playerid, PlayerInfo[playerid][pXPos], PlayerInfo[playerid][pYPos], PlayerInfo[playerid][pZPos]);
	
	GetPlayerWeaponData(playerid, 0, PlayerInfo[playerid][pWeapon1], PlayerInfo[playerid][pAmmo1]);
	GetPlayerWeaponData(playerid, 1, PlayerInfo[playerid][pWeapon2], PlayerInfo[playerid][pAmmo2]);
	GetPlayerWeaponData(playerid, 2, PlayerInfo[playerid][pWeapon3], PlayerInfo[playerid][pAmmo3]);
	GetPlayerWeaponData(playerid, 3, PlayerInfo[playerid][pWeapon4], PlayerInfo[playerid][pAmmo4]);
	GetPlayerWeaponData(playerid, 4, PlayerInfo[playerid][pWeapon5], PlayerInfo[playerid][pAmmo5]);
	GetPlayerWeaponData(playerid, 5, PlayerInfo[playerid][pWeapon6], PlayerInfo[playerid][pAmmo6]);
	GetPlayerWeaponData(playerid, 6, PlayerInfo[playerid][pWeapon7], PlayerInfo[playerid][pAmmo7]);
	GetPlayerWeaponData(playerid, 7, PlayerInfo[playerid][pWeapon8], PlayerInfo[playerid][pAmmo8]);
	GetPlayerWeaponData(playerid, 8, PlayerInfo[playerid][pWeapon9], PlayerInfo[playerid][pAmmo9]);
	GetPlayerWeaponData(playerid, 9, PlayerInfo[playerid][pWeapon10], PlayerInfo[playerid][pAmmo10]);
	GetPlayerWeaponData(playerid, 10, PlayerInfo[playerid][pWeapon11], PlayerInfo[playerid][pAmmo11]);
	GetPlayerWeaponData(playerid, 11, PlayerInfo[playerid][pWeapon12], PlayerInfo[playerid][pAmmo12]);
	GetPlayerWeaponData(playerid, 12, PlayerInfo[playerid][pWeapon13], PlayerInfo[playerid][pAmmo13]);
	GetPlayerWeaponData(playerid, 13, PlayerInfo[playerid][pWeapon14], PlayerInfo[playerid][pAmmo14]);
	
    GetPlayerHealth(playerid, PlayerInfo[playerid][pHealth]);
    INI_WriteInt(File, "Cash",GetPlayerCash(playerid));
    INI_WriteInt(File, "Admin",PlayerInfo[playerid][pAdmin]);
    INI_WriteInt(File, "Kills",PlayerInfo[playerid][pKills]);
    INI_WriteInt(File, "Deaths",PlayerInfo[playerid][pDeaths]);
    INI_WriteInt(File, "LSD",PlayerInfo[playerid][dLSD]);
    INI_WriteInt(File, "BizID",PlayerInfo[playerid][BizID]);
    INI_WriteInt(File, "Cocaine",PlayerInfo[playerid][dCocaine]);
    INI_WriteInt(File, "Marijuana",PlayerInfo[playerid][dMarijuana]);
    INI_WriteInt(File, "Respect",PlayerInfo[playerid][pRespect]);
    INI_WriteInt(File, "Cigarettes",PlayerInfo[playerid][pCigarettes]);
    INI_WriteInt(File, "Beer",PlayerInfo[playerid][pBeer]);
    INI_WriteInt(File, "BankAccount",PlayerInfo[playerid][pBankAccount]);
    INI_WriteInt(File, "Datasaved",PlayerInfo[playerid][pAccountdata]);
    INI_WriteInt(File, "Number",PlayerInfo[playerid][pNumber]);
    INI_WriteInt(File, "Skin", PlayerInfo[playerid][pSkin]);
    INI_WriteInt(File, "Level",PlayerInfo[playerid][pLevel]);
    INI_WriteInt(File, "Weapon1",PlayerInfo[playerid][pWeapon1]);
    INI_WriteInt(File, "Weapon2",PlayerInfo[playerid][pWeapon2]);
    INI_WriteInt(File, "Weapon3",PlayerInfo[playerid][pWeapon3]);
    INI_WriteInt(File, "Weapon4",PlayerInfo[playerid][pWeapon4]);
    INI_WriteInt(File, "Weapon5",PlayerInfo[playerid][pWeapon5]);
    INI_WriteInt(File, "Weapon6",PlayerInfo[playerid][pWeapon6]);
    INI_WriteInt(File, "Weapon7",PlayerInfo[playerid][pWeapon7]);
    INI_WriteInt(File, "Weapon8",PlayerInfo[playerid][pWeapon8]);
    INI_WriteInt(File, "Weapon9",PlayerInfo[playerid][pWeapon9]);
    INI_WriteInt(File, "Weapon10",PlayerInfo[playerid][pWeapon10]);
    INI_WriteInt(File, "Weapon11",PlayerInfo[playerid][pWeapon11]);
    INI_WriteInt(File, "Weapon12",PlayerInfo[playerid][pWeapon12]);
    INI_WriteInt(File, "Weapon13",PlayerInfo[playerid][pWeapon13]);
    INI_WriteInt(File, "Weapon14",PlayerInfo[playerid][pWeapon14]);
    INI_WriteInt(File, "Ammo1",PlayerInfo[playerid][pAmmo1]);
    INI_WriteInt(File, "Ammo2",PlayerInfo[playerid][pAmmo2]);
    INI_WriteInt(File, "Ammo3",PlayerInfo[playerid][pAmmo3]);
    INI_WriteInt(File, "Ammo4",PlayerInfo[playerid][pAmmo4]);
    INI_WriteInt(File, "Ammo5",PlayerInfo[playerid][pAmmo5]);
    INI_WriteInt(File, "Ammo6",PlayerInfo[playerid][pAmmo6]);
    INI_WriteInt(File, "Ammo7",PlayerInfo[playerid][pAmmo7]);
    INI_WriteInt(File, "Ammo8",PlayerInfo[playerid][pAmmo8]);
    INI_WriteInt(File, "Ammo9",PlayerInfo[playerid][pAmmo9]);
    INI_WriteInt(File, "Ammo10",PlayerInfo[playerid][pAmmo10]);
    INI_WriteInt(File, "Ammo11",PlayerInfo[playerid][pAmmo11]);
    INI_WriteInt(File, "Ammo12",PlayerInfo[playerid][pAmmo12]);
    INI_WriteInt(File, "Ammo13",PlayerInfo[playerid][pAmmo13]);
    INI_WriteInt(File, "Ammo14",PlayerInfo[playerid][pAmmo14]);
    INI_WriteInt(File, "BusinessMoney",PlayerInfo[playerid][BusinessMoney]);
    INI_WriteFloat(File, "Health", PlayerInfo[playerid][pHealth]);
   	INI_WriteInt(File, "DriverLicense",PlayerInfo[playerid][pDriverLicense]);
   	INI_WriteInt(File, "Age",PlayerInfo[playerid][pAge]);
	INI_WriteInt(File, "Gender",PlayerInfo[playerid][pGender]);
	INI_WriteInt(File, "InJail",PlayerInfo[playerid][pInJail]);
	INI_WriteInt(File, "InJailTime",PlayerInfo[playerid][pInJailTime]);
 	INI_WriteInt(File, "HouseID", PlayerInfo[playerid][HouseID]);
	INI_WriteInt(File, "Mask",PlayerInfo[playerid][pMask]);
	INI_WriteInt(File, "FightingStyle",PlayerInfo[playerid][pFightingStyle]);
	INI_WriteInt(File, "Boombox",PlayerInfo[playerid][pBoombox]);
	INI_WriteInt(File, "Experience", PlayerInfo[playerid][pExperience]);
    INI_Close(File);
    
    if(GetPVarType(playerid, "PlacedBB"))
    {
        DestroyDynamicObject(GetPVarInt(playerid, "PlacedBB"));
        DestroyDynamic3DTextLabel(Text3D:GetPVarInt(playerid, "BBLabel"));
        if(GetPVarType(playerid, "BBArea"))
        {
            foreach(Player,i)
            {
                if(IsPlayerInDynamicArea(i, GetPVarInt(playerid, "BBArea")))
                {
                    StopAudioStreamForPlayer(i);
                    SCM(i, COLOR_LIGHTBLUE, " The boombox creator has disconnected from the server.");
                }
            }
        }
    }
    
    if(IsBeingSpeced[playerid] == 1)//If the player being spectated, disconnects, then turn off the spec mode for the spectator.
    {
        foreach(Player,i)
        {
            if(spectatorid[i] == playerid)
            {
                TogglePlayerSpectating(i,false);// This justifies what's above, if it's not off then you'll be either spectating your connect screen, or somewhere in blueberry (I don't know why)
            }
        }
    }
    return 1;
}

public OnPlayerRequestClass(playerid,classid)
{
   	TextDrawShowForPlayer(playerid,Textdraw0);
   	TextDrawShowForPlayer(playerid,Textdraw1);
	for(new i = 0; i < 50; i++) SCM(playerid, COLOR_WHITE," ");
	SetPlayerCameraPos(playerid, 1982.5140,-1703.8862,124.3137);
	SetPlayerCameraLookAt(playerid, 1765.5276,-1451.8524,137.7477);
 	if(fexist(UserPath(playerid)))
    {
        INI_ParseFile(UserPath(playerid), "LoadUser_%s", .bExtra = true, .extra = playerid);
        ShowPlayerDialog(playerid, DIALOG_LOGIN, DIALOG_STYLE_INPUT,"Login","Welcome back to Illusional Roleplay, please type in your password to log in.","Login","Quit");
    }
    else
    {
        ShowPlayerDialog(playerid, DIALOG_REGISTER, DIALOG_STYLE_INPUT,"Register","Welcome to Illusional Roleplay.\nTo register an account please type in your desired password below.","Register","Quit");
    }
    return 1;
}

public OnPlayerSpawn(playerid)
{

	TextDrawShowForPlayer(playerid,txtTimeDisp);

	gettime(hour, minute);
	SetPlayerTime(playerid,hour,minute);
	TextDrawHideForPlayer(playerid,Textdraw0);
   	TextDrawHideForPlayer(playerid,Textdraw1);

	LoadPlayerSpawnData(playerid);
	FadeColorForPlayer(playerid,0,0,0,255,0,0,0,0,15,0);
	
	if(isAlive[playerid] == false)
	{
	    SetPlayerPos(playerid, Deadx[playerid], Deady[playerid], Deadz[playerid]);
		stopanimAllowed[playerid] = false;
	    SCM(playerid, COLOR_LIGHTRED, "* You're currently brutally wounded. If no-one helps you, you will die. /acceptdeath if you wish to re-spawn.");
     	TogglePlayerControllable(playerid,0);
 	    SetTimerEx("LoadDeathAnim", 500, false, "i", playerid);
	    return 1;
	}

	if(PlayerInfo[playerid][pInJail] == 1)
	{
	    new string[64];
	   	SetPlayerPos(playerid, 1492.2151,-1768.2281,3285.2859);
	   	format(string, sizeof(string), "* Your character is currently is jail for another %d seconds.", PlayerInfo[playerid][pInJailTime]);
	   	SCM(playerid, COLOR_LIGHTRED, string);
	}
	if(IsSpecing[playerid] == 1)
    {
        SetPlayerPos(playerid,SpecX[playerid],SpecY[playerid],SpecZ[playerid]);// Remember earlier we stored the positions in these variables, now we're gonna get them from the variables.
        SetPlayerInterior(playerid,Inter[playerid]);//Setting the player's interior to when they typed '/spec'
        SetPlayerVirtualWorld(playerid,vWorld[playerid]);//Setting the player's virtual world to when they typed '/spec'
        IsSpecing[playerid] = 0;//Just saying you're free to use '/spec' again YAY :D
        IsBeingSpeced[spectatorid[playerid]] = 0;//Just saying that the player who was being spectated, is not free from your stalking >:D
    }
    return 1;
}

public PlayerActionMessage(playerid,Float:radius,message[])
{
	new
	string[128];
	
	format(string, sizeof(string), "* %s %s", GetName(playerid), message);
	ProxDetector(20.0, playerid, string, COLOR_PURPLE, COLOR_PURPLE, COLOR_PURPLE, COLOR_PURPLE, COLOR_PURPLE);
	return 1;
}

public OnPlayerStateChange(playerid, newstate, oldstate)
{
	if(IsPlayerInAnyVehicle(playerid) && !IsBicycle(GetPlayerVehicleID(playerid)))
	{
		//TextDrawShowForPlayer(playerid, SpeedoBox);
		TextDrawShowForPlayer(playerid, SpeedoText[playerid]);
		new vehicleid = GetPlayerVehicleID(playerid);
		if(VehicleSecurity[vehicleid] == 1)
		{
			ToggleAlarm(vehicleid, VEHICLE_PARAMS_ON);
			SetTimerEx("StopAlarm", ALARM_TIME, false, "d", vehicleid);
		}
	}
	else
	{
		//TextDrawHideForPlayer(playerid, SpeedoBox);
		TextDrawHideForPlayer(playerid, SpeedoText[playerid]);
	}
	if(newstate == PLAYER_STATE_DRIVER)
	{
		new vehicleid = GetPlayerVehicleID(playerid);
		new id = GetVehicleID(vehicleid);
		if(IsValidVehicle(id))
		{
			if(VehicleCreated[id] == VEHICLE_DEALERSHIP)
			{
				SetPVarInt(playerid, "DialogValue1", id);
				ShowDialog(playerid, DIALOG_VEHICLE_BUY);
				return 1;
			}
		}
		if(IsBicycle(vehicleid))
		{
			ToggleEngine(vehicleid, VEHICLE_PARAMS_ON);
		}
		if(Fuel[vehicleid] <= 0)
		{
			ToggleEngine(vehicleid, VEHICLE_PARAMS_OFF);
		}
	}
    if(newstate == PLAYER_STATE_DRIVER)
    {
		for(new i=0; i<5; i++)
		{
			if(IsPlayerInVehicle(playerid, DMVcar[i]))
			{
  				if(PlayerInfo[playerid][pDriverLicense] == 0)
  				{
        			if(TakingDriverLicense[playerid] == true)
        			{
        				SetPlayerCheckpoint(playerid, 2050.4858,-1929.8646,13.2555, 3.0);
	        			DMVcp[playerid] = 1;
	    			    TakingDriverLicense[playerid] = false;
	    			    SCM(playerid, COLOR_GOLD, "* Drive through all of the checkpoints slowly to pass the test. Check your mini-map if you can't see the checkpoints.");
	    			    SCM(playerid, COLOR_WHITE, "* If you leave the vehicle it will respawn.");
					}
					else
					{
					    RemovePlayerFromVehicle(playerid);
					    SCM(playerid, COLOR_LIGHTRED, "[Error]: You are not taking a driver-license test.");
					}
				}
				else
				{
    				RemovePlayerFromVehicle(playerid);
				    SCM(playerid, COLOR_LIGHTRED, "[Error]: You already have a drivers license.");
				}
            }
        }
    }
    if(newstate == PLAYER_STATE_DRIVER)
    {
		for(new i=0; i<5; i++)
		{
			if(IsPlayerInVehicle(playerid, rentCAR[i]))
			{
			    if(rentingVehicle[playerid] == false)
			    {
					SCM(playerid, COLOR_GOLD, "* You can /rentcar this vehicle for $10.");
					TogglePlayerControllable(playerid,0);
				}
				else return SCM(playerid, COLOR_LIGHTRED, "* You're already renting a vehicle. /unrentcar.");
			}
        }
    }
    if(newstate == PLAYER_STATE_DRIVER)// If the player's state changes to a vehicle state we'll have to spec the vehicle.
    {
		if(PlayerInfo[playerid][pDriverLicense] == 0)
		{
		    SCM(playerid, COLOR_LIGHTRED, "* You do not have a drivers license, watch out for the police.");
		    return 1;
		}
    }
    if(newstate == PLAYER_STATE_DRIVER || newstate == PLAYER_STATE_PASSENGER)// If the player's state changes to a vehicle state we'll have to spec the vehicle.
    {
        if(IsBeingSpeced[playerid] == 1)//If the player being spectated, enters a vehicle, then let the spectator spectate the vehicle.
        {
            foreach(Player,i)
            {
                if(spectatorid[i] == playerid)
                {
                    PlayerSpectateVehicle(i, GetPlayerVehicleID(playerid));// Letting the spectator, spectate the vehicle of the player being spectated (I hope you understand this xD)
                }
            }
        }
    }
    if(newstate == PLAYER_STATE_ONFOOT)
    {
        if(IsBeingSpeced[playerid] == 1)//If the player being spectated, exists a vehicle, then let the spectator spectate the player.
        {
            foreach(Player,i)
            {
                if(spectatorid[i] == playerid)
                {
                    PlayerSpectatePlayer(i, playerid);// Letting the spectator, spectate the player who exited the vehicle.
                }
            }
        }
    }
	return 1;
}

public OnPlayerExitVehicle(playerid, vehicleid)
{
	for(new i=0; i<5; i++)
	{
		if(IsPlayerInVehicle(playerid, DMVcar[i]))
		{
			new vehicle;
			vehicle = GetPlayerVehicleID(playerid);
			SetVehicleToRespawn(vehicle);
			DisablePlayerCheckpoint(playerid);
			SCM(playerid, COLOR_LIGHTRED, "[Error]: You can't leave the DMV vehicle while taking a test.");
		}
	}
	
	for(new i=0; i<5; i++)
	{
		if(IsPlayerInVehicle(playerid, rentCAR[i]))
		{
			new vehicle;
			vehicle = GetPlayerVehicleID(playerid);
			SetVehicleToRespawn(vehicle);
			SCM(playerid, COLOR_GOLD, "* Your rental vehicle has been respawned. (to give a chance for other players to rent cars).");
			rentingVehicle[playerid] = false;
			TogglePlayerControllable(playerid,1);
		}
	}
    return 1;
}

public OnPlayerKeyStateChange(playerid, newkeys, oldkeys)
{
    return 1;
}

public OnDialogResponse(playerid, dialogid, response, listitem, inputtext[])
{
    if(dialogid == 75)
    {
    	if(!response)
     	{
        	return 1;
        }
		switch(listitem)
  		{
    		case 0:
      		{
      		    ShowPlayerDialog(playerid,DIALOG_BOOMBOX1,DIALOG_STYLE_LIST,"Jazz","Smooth Jazz\nBay Smooth Jazz","Select","Cancel");
            }
            case 1:
            {
                ShowPlayerDialog(playerid,DIALOG_BOOMBOX2,DIALOG_STYLE_LIST,"Pop","Radio Sound Pop\n70's and 80's POP","Select","Cancel");
            }
            case 2:
            {
                ShowPlayerDialog(playerid,DIALOG_BOOMBOX3,DIALOG_STYLE_LIST,"Hip-Hop","Old School Hip-Hop\nHip-Hop/Rap","Select","Cancel");
            }
            case 3:
            {
                ShowPlayerDialog(playerid,DIALOG_BOOMBOX4,DIALOG_STYLE_LIST,"R&B","True R&B\nFlow 103","Select","Cancel");
			}
			case 4:
			{
			    ShowPlayerDialog(playerid,DIALOG_BOOMBOX5,DIALOG_STYLE_LIST,"Rock","Classic Rock\nMetal","Select","Cancel");
			}
			case 5:
			{
			    ShowPlayerDialog(playerid,DIALOG_BOOMBOX6,DIALOG_STYLE_LIST,"Country","181 Kicking Country\nAbsolute Country Radio","Select","Cancel");
			}
			case 6:
			{
			    ShowPlayerDialog(playerid,DIALOG_BOOMBOX7,DIALOG_STYLE_INPUT, "Boombox Input URL", "Please put a Music URL to play the Music", "Play", "Cancel");
			}
			case 7:
			{
                if(GetPVarType(playerid, "BBArea"))
			    {
			        PlayerActionMessage(playerid,20.0, "turns his boombox off.");
			        foreach(Player, i)
					{
			            if(IsPlayerInDynamicArea(i, GetPVarInt(playerid, "BBArea")))
			            {
			                StopStream(i);
						}
					}
			        DeletePVar(playerid, "BBStation");
				}
			}
        }
		return 1;
	}
	if(dialogid == DIALOG_BOOMBOX1)//JAZZ
	{
	    if(!response)
	    {
     		ShowPlayerDialog(playerid,DIALOG_BOOMBOX,DIALOG_STYLE_LIST,"Radio List","Jazz\nPop\nHip-Hop\nR&B and Urban\nRock\nCountry\nEnter URL\nTurn Off Boombox","Select", "Cancel");
		}
		if(response)
        {
            if(listitem == 0)
            {
                if(GetPVarType(playerid, "PlacedBB"))
				{
				    foreach(Player, i)
					{
						if(IsPlayerInDynamicArea(i, GetPVarInt(playerid, "BBArea")))
						{
							PlayStream(i, "http://yp.shoutcast.com/sbin/tunein-station.pls?id=467000", GetPVarFloat(playerid, "BBX"), GetPVarFloat(playerid, "BBY"), GetPVarFloat(playerid, "BBZ"), 30.0, 1);
				  		}
				  	}
			  		SetPVarString(playerid, "BBStation", "http://yp.shoutcast.com/sbin/tunein-station.pls?id=467000");
				}
			}
		 	if(listitem == 1)
            {
                if(GetPVarType(playerid, "PlacedBB"))
				{
				    foreach(Player, i)
					{
						if(IsPlayerInDynamicArea(i, GetPVarInt(playerid, "BBArea")))
						{
							PlayStream(i, "http://yp.shoutcast.com/sbin/tunein-station.pls?id=1009184", GetPVarFloat(playerid, "BBX"), GetPVarFloat(playerid, "BBY"), GetPVarFloat(playerid, "BBZ"), 30.0, 1);
				  		}
				  	}
			  		SetPVarString(playerid, "BBStation", "http://yp.shoutcast.com/sbin/tunein-station.pls?id=1009184");
				}
			}
		}
		return 1;
	}
	if(dialogid == DIALOG_BOOMBOX2)//POP
	{
	    if(!response)
	    {
   			ShowPlayerDialog(playerid,DIALOG_BOOMBOX,DIALOG_STYLE_LIST,"Radio List","Jazz\nPop\nHip-Hop\nR&B and Urban\nRock\nCountry\nEnter URL\nTurn Off Boombox","Select", "Cancel");
		}
		if(response)
        {
            if(listitem == 0)
            {
                if(GetPVarType(playerid, "PlacedBB"))
				{
				    foreach(Player, i)
					{
						if(IsPlayerInDynamicArea(i, GetPVarInt(playerid, "BBArea")))
						{
							PlayStream(i, "http://yp.shoutcast.com/sbin/tunein-station.pls?id=16101", GetPVarFloat(playerid, "BBX"), GetPVarFloat(playerid, "BBY"), GetPVarFloat(playerid, "BBZ"), 30.0, 1);
				  		}
				  	}
			  		SetPVarString(playerid, "BBStation", "http://yp.shoutcast.com/sbin/tunein-station.pls?id=16101");
				}
			}
			if(listitem == 1)
            {
                if(GetPVarType(playerid, "PlacedBB"))
				{
				    foreach(Player, i)
					{
						if(IsPlayerInDynamicArea(i, GetPVarInt(playerid, "BBArea")))
						{
							PlayStream(i, "http://yp.shoutcast.com/sbin/tunein-station.pls?id=186485", GetPVarFloat(playerid, "BBX"), GetPVarFloat(playerid, "BBY"), GetPVarFloat(playerid, "BBZ"), 30.0, 1);
				  		}
				  	}
			  		SetPVarString(playerid, "BBStation", "http://yp.shoutcast.com/sbin/tunein-station.pls?id=186485");
				}
			}
		}
		return 1;
	}
	if(dialogid == DIALOG_BOOMBOX3)//HIP-HOP
	{
	    if(!response)
	    {
     		ShowPlayerDialog(playerid,DIALOG_BOOMBOX,DIALOG_STYLE_LIST,"Radio List","Jazz\nPop\nHip-Hop\nR&B and Urban\nRock\nCountry\nEnter URL\nTurn Off Boombox","Select", "Cancel");
		}
		if(response)
        {
            if(listitem == 0)
            {
                if(GetPVarType(playerid, "PlacedBB"))
				{
        			foreach(Player, i)
					{
						if(IsPlayerInDynamicArea(i, GetPVarInt(playerid, "BBArea")))
						{
							PlayStream(i, "http://yp.shoutcast.com/sbin/tunein-station.pls?id=355909", GetPVarFloat(playerid, "BBX"), GetPVarFloat(playerid, "BBY"), GetPVarFloat(playerid, "BBZ"), 30.0, 1);
				  		}
				  	}
			  		SetPVarString(playerid, "BBStation", "http://yp.shoutcast.com/sbin/tunein-station.pls?id=355909");
    			}
   			}
   			if(listitem == 1)
            {
                if(GetPVarType(playerid, "PlacedBB"))
				{
				    foreach(Player, i)
					{
						if(IsPlayerInDynamicArea(i, GetPVarInt(playerid, "BBArea")))
						{
							PlayStream(i, "http://yp.shoutcast.com/sbin/tunein-station.pls?id=190767", GetPVarFloat(playerid, "BBX"), GetPVarFloat(playerid, "BBY"), GetPVarFloat(playerid, "BBZ"), 30.0, 1);
				  		}
				  	}
			  		SetPVarString(playerid, "BBStation", "http://yp.shoutcast.com/sbin/tunein-station.pls?id=190767");
				}
			}
		}
		return 1;
	}
	if(dialogid == DIALOG_BOOMBOX4)//R&B
	{
	    if(!response)
	    {
     		ShowPlayerDialog(playerid,DIALOG_BOOMBOX,DIALOG_STYLE_LIST,"Radio List","Jazz\nPop\nHip-Hop\nR&B and Urban\nRock\nCountry\nEnter URL\nTurn Off Boombox","Select", "Cancel");
		}
		if(response)
        {
            if(listitem == 0)
            {
                if(GetPVarType(playerid, "PlacedBB"))
				{
				    foreach(Player, i)
					{
						if(IsPlayerInDynamicArea(i, GetPVarInt(playerid, "BBArea")))
						{
							PlayStream(i, "http://yp.shoutcast.com/sbin/tunein-station.pls?id=366480", GetPVarFloat(playerid, "BBX"), GetPVarFloat(playerid, "BBY"), GetPVarFloat(playerid, "BBZ"), 30.0, 1);
				  		}
				  	}
			  		SetPVarString(playerid, "BBStation", "http://yp.shoutcast.com/sbin/tunein-station.pls?id=366480");
				}
			}
			if(listitem == 1)
            {
                if(GetPVarType(playerid, "PlacedBB"))
				{
				    foreach(Player, i)
					{
						if(IsPlayerInDynamicArea(i, GetPVarInt(playerid, "BBArea")))
						{
							PlayStream(i, "http://yp.shoutcast.com/sbin/tunein-station.pls?id=293191", GetPVarFloat(playerid, "BBX"), GetPVarFloat(playerid, "BBY"), GetPVarFloat(playerid, "BBZ"), 30.0, 1);
				  		}
				  	}
			  		SetPVarString(playerid, "BBStation", "http://yp.shoutcast.com/sbin/tunein-station.pls?id=293191");
				}
			}
		}
		return 1;
	}
	if(dialogid == DIALOG_BOOMBOX5)//ROCK
	{
	    if(!response)
	    {
     		ShowPlayerDialog(playerid,DIALOG_BOOMBOX,DIALOG_STYLE_LIST,"Radio List","Jazz\nPop\nHip-Hop\nR&B and Urban\nRock\nCountry\nEnter URL\nTurn Off Boombox","Select", "Cancel");
		}
		if(response)
        {
            if(listitem == 0)
            {
                if(GetPVarType(playerid, "PlacedBB"))
				{
				    foreach(Player, i)
					{
						if(IsPlayerInDynamicArea(i, GetPVarInt(playerid, "BBArea")))
						{
							PlayStream(i, "http://www.181.fm/stream/asx/181-eagle", GetPVarFloat(playerid, "BBX"), GetPVarFloat(playerid, "BBY"), GetPVarFloat(playerid, "BBZ"), 30.0, 1);
				  		}
				  	}
			  		SetPVarString(playerid, "BBStation", "http://www.181.fm/stream/asx/181-eagle");
				}
			}
   			if(listitem == 1)
            {
                if(GetPVarType(playerid, "PlacedBB"))
				{
				    foreach(Player, i)
					{
						if(IsPlayerInDynamicArea(i, GetPVarInt(playerid, "BBArea")))
						{
							PlayStream(i, "http://yp.shoutcast.com/sbin/tunein-station.pls?id=558051", GetPVarFloat(playerid, "BBX"), GetPVarFloat(playerid, "BBY"), GetPVarFloat(playerid, "BBZ"), 30.0, 1);
				  		}
				  	}
			  		SetPVarString(playerid, "BBStation", "http://yp.shoutcast.com/sbin/tunein-station.pls?id=558051");
				}
			}
		}
		return 1;
	}
	if(dialogid == DIALOG_BOOMBOX6)//COUNTRY
	{
	    if(!response)
	    {
	       ShowPlayerDialog(playerid,DIALOG_BOOMBOX,DIALOG_STYLE_LIST,"Radio List","Jazz\nPop\nHip-Hop\nR&B and Urban\nRock\nCountry\nEnter URL\nTurn Off Boombox","Select", "Cancel");
		}
		if(response)
        {
            if(listitem == 0)
            {
                if(GetPVarType(playerid, "PlacedBB"))
				{
				    foreach(Player, i)
					{
						if(IsPlayerInDynamicArea(i, GetPVarInt(playerid, "BBArea")))
						{
							PlayStream(i, "http://yp.shoutcast.com/sbin/tunein-station.pls?id=221956", GetPVarFloat(playerid, "BBX"), GetPVarFloat(playerid, "BBY"), GetPVarFloat(playerid, "BBZ"), 30.0, 1);
				  		}
				  	}
			  		SetPVarString(playerid, "BBStation", "http://yp.shoutcast.com/sbin/tunein-station.pls?id=221956");
				}
			}
   			if(listitem == 1)
            {
                if(GetPVarType(playerid, "PlacedBB"))
				{
				    foreach(Player, i)
					{
						if(IsPlayerInDynamicArea(i, GetPVarInt(playerid, "BBArea")))
						{
							PlayStream(i, "http://yp.shoutcast.com/sbin/tunein-station.pls?id=1050709", GetPVarFloat(playerid, "BBX"), GetPVarFloat(playerid, "BBY"), GetPVarFloat(playerid, "BBZ"), 30.0, 1);
				  		}
				  	}
			  		SetPVarString(playerid, "BBStation", "http://yp.shoutcast.com/sbin/tunein-station.pls?id=1050709");
				}
			}
		}
		return 1;
	}
	if(dialogid == DIALOG_BOOMBOX7)//SET URL
	{
		if(response == 1)
		{
		    if(isnull(inputtext))
		    {
		        SCM(playerid, COLOR_LIGHTRED, "[Error]: You didn't type in any URL.");
		        return 1;
		    }
		    if(strlen(inputtext))
		    {
		        if(GetPVarType(playerid, "PlacedBB"))
				{
				    foreach(Player, i)
					{
						if(IsPlayerInDynamicArea(i, GetPVarInt(playerid, "BBArea")))
						{
							PlayStream(i, inputtext, GetPVarFloat(playerid, "BBX"), GetPVarFloat(playerid, "BBY"), GetPVarFloat(playerid, "BBZ"), 30.0, 1);
				  		}
				  	}
			  		SetPVarString(playerid, "BBStation", inputtext);
				}
			}
		}
		return 1;
	}
    switch( dialogid )
    {
	   	case DIALOG_DRUGSNGUNS:
      	  {
  		        switch(listitem)
   		    {
    	    	   case 0:
     	   	   {
       	    		ShowPlayerDialog(playerid, 10, DIALOG_STYLE_LIST, "What kind of drugs, homie?", "(10g)Marijuana($50)\n(10g)Cocaine($300)\n(5g)LSD($50)", "Choose", "Cancel");
    	    	   }
    	    	   case 1:
    	    	   {
	       	    	   ShowPlayerDialog(playerid, 15, DIALOG_STYLE_LIST, "What kind of weapons, homie?", "Knife($100)\nBaseball Bat($50)", "Choose", "Cancel");
    	    	   }
			}
		}
		case DIALOG_USE:
  		{
           	switch(listitem)
        	{
        	    case 0:
        	    {

    				if (PlayerInfo[playerid][pBeer] < 1) return SCM(playerid, COLOR_LIGHTRED, "[Error]: You do not have any beers.");

				    SetPlayerSpecialAction(playerid,SPECIAL_ACTION_DRINK_BEER);
				    IsDrinkingBeer[playerid] = 1;
				    

				    PlayerInfo[playerid][pBeer] -= 1;
        	    }
        	    case 1:
        	    {
    				if (PlayerInfo[playerid][pCigarettes] < 1) return SCM(playerid, COLOR_LIGHTRED, "[Error]: You do not have any cigarettes.");

				    SetPlayerSpecialAction(playerid,SPECIAL_ACTION_SMOKE_CIGGY);
				    IsSmokingCigarette[playerid] = 1;
				    

				    PlayerInfo[playerid][pCigarettes] -= 1;
				    PlayerActionMessage(playerid,15.0,"lights up a cigarette.");
        	    }
        	    case 2:
        	    {
	            	ShowPlayerDialog(playerid, DIALOG_DRUGS, DIALOG_STYLE_LIST, "Drugs", "Marijuana\nCocaine\nLSD", "Next", "Cancel");
				}
        	    case 3:
        	    {
                    ShowPlayerDialog(playerid, 76, DIALOG_STYLE_LIST, "Boombox", "Use\nChange Channel\nPickup", "Use", "Cancel");
        	    }
			}
		}
		case DIALOG_BUY:
  		{
           	switch(listitem)
        	{
          	  	case 0:
        	    {
					if(GetPlayerCash(playerid) < 14) return SCM(playerid, COLOR_LIGHTRED, "* You do not have enough money.");
					PlayerInfo[playerid][pBeer] += 6;
					if(PlayerInfo[playerid][pAge] < 16) return SCM(playerid, COLOR_LIGHTRED, "[Error]: You're not old enough to buy beer.");
					SCM(playerid, COLOR_GOLD, "* You have bought a six-pack of beers, /use.");
        	    }
         	  	case 1:
        	    {
					if(GetPlayerCash(playerid) < 4) return SCM(playerid, COLOR_LIGHTRED, "* You do not have enough money.");
					PlayerInfo[playerid][pCigarettes] += 20;
					if(PlayerInfo[playerid][pAge] < 18) return SCM(playerid, COLOR_LIGHTRED, "[Error]: You're not old enough to buy cigarettes");
					SCM(playerid, COLOR_GOLD, "* You have bought a packet of cigarettes, /use.");
        	    }
        	    case 2:
        	    {
					if(GetPlayerCash(playerid) < 0) return SCM(playerid, COLOR_LIGHTRED, "* You do not have enough money.");
					SCM(playerid, COLOR_GOLD, "* You have bought a dice, /dice.");
					Dice[playerid] = 1;
        	    }
        	    case 3:
        	    {
					if(GetPlayerCash(playerid) < 49) return SCM(playerid, COLOR_LIGHTRED, "* You do not have enough money.");
					PlayerInfo[playerid][pMask] = 1;
					SCM(playerid, COLOR_GOLD, "* You have bought a mask, /mask to put it on/off.");
        	    }
        	    case 4:
        	    {
					if(GetPlayerCash(playerid) < 49) return SCM(playerid, COLOR_LIGHTRED, "* You do not have enough money.");
					PlayerInfo[playerid][dWater] = 5;
					SCM(playerid, COLOR_GOLD, "* You have bought a water bottle. /waterplant to make your marijuana-plant grow.");
        	    }
			}
		}
		case DIALOG_TRAIN:
  		{
           	switch(listitem)
        	{
          	  	case 0:
        	    {
					if(GetPlayerCash(playerid) < 9) return SCM(playerid, COLOR_LIGHTRED, "* You do not have enough money.");
					PlayerInfo[playerid][pFightingStyle] = 1;
					SetPlayerFightingStyle (playerid, FIGHT_STYLE_NORMAL);
					
					SCM(playerid, COLOR_GOLD, "* You have learned the normal fightingstyle.");
        	    }
         	  	case 1:
        	    {
					if(GetPlayerCash(playerid) < 19) return SCM(playerid, COLOR_LIGHTRED, "* You do not have enough money.");
					PlayerInfo[playerid][pFightingStyle] = 2;
					SetPlayerFightingStyle (playerid, FIGHT_STYLE_BOXING);
					SCM(playerid, COLOR_GOLD, "* You have learned boxing.");
        	    }
        	    case 2:
        	    {
					if(GetPlayerCash(playerid) < 19) return SCM(playerid, COLOR_LIGHTRED, "* You do not have enough money.");
					PlayerInfo[playerid][pFightingStyle] = 3;
					SetPlayerFightingStyle (playerid, FIGHT_STYLE_KNEEHEAD);
					SCM(playerid, COLOR_GOLD, "* You have learned the kneehead fightingstyle.");
        	    }
        	    case 3:
        	    {
					if(GetPlayerCash(playerid) < 19) return SCM(playerid, COLOR_LIGHTRED, "* You do not have enough money.");
					PlayerInfo[playerid][pFightingStyle] = 4;
					SetPlayerFightingStyle (playerid, FIGHT_STYLE_KUNGFU);
					SCM(playerid, COLOR_GOLD, "* You have learned the kung-fu fightingstyle.");
        	    }
			}
		}
		case DIALOG_GENDER:
  		{
           	switch(listitem)
        	{
          	  	case 0:
        	    {
					if(playerRace[playerid] == 1)
					{
						PlayerInfo[playerid][pGender] = 0;
						SetTimerEx("TutorialDone", 1000, false, "i", playerid);
						SetPlayerSkin(playerid, 48);
						PlayerInfo[playerid][pSkin] = 48;
					}
					else if(playerRace[playerid] == 2)
					{
						PlayerInfo[playerid][pGender] = 0;
						SetTimerEx("TutorialDone", 1000, false, "i", playerid);
						SetPlayerSkin(playerid, 28);
						PlayerInfo[playerid][pSkin] = 28;
					}
					else if(playerRace[playerid] == 3)
					{
						PlayerInfo[playerid][pGender] = 0;
						SetTimerEx("TutorialDone", 1000, false, "i", playerid);
						SetPlayerSkin(playerid, 60);
						PlayerInfo[playerid][pSkin] = 60;
					}
					else if(playerRace[playerid] == 4)
					{
						PlayerInfo[playerid][pGender] = 0;
						SetTimerEx("TutorialDone", 1000, false, "i", playerid);
						SetPlayerSkin(playerid, 120);
						PlayerInfo[playerid][pSkin] = 120;
					}
        	    }
         	  	case 1:
        	    {
					if(playerRace[playerid] == 1)
					{
						PlayerInfo[playerid][pGender] = 1;
						SetTimerEx("TutorialDone", 1000, false, "i", playerid);
						SetPlayerSkin(playerid, 12);
						PlayerInfo[playerid][pSkin] = 12;
					}
					else if(playerRace[playerid] == 2)
					{
						PlayerInfo[playerid][pGender] = 1;
						SetTimerEx("TutorialDone", 1000, false, "i", playerid);
						SetPlayerSkin(playerid, 13);
						PlayerInfo[playerid][pSkin] = 13;
					}
					else if(playerRace[playerid] == 3)
					{
						PlayerInfo[playerid][pGender] = 1;
						SetTimerEx("TutorialDone", 1000, false, "i", playerid);
						SetPlayerSkin(playerid, 93);
						PlayerInfo[playerid][pSkin] = 93;
					}
					else if(playerRace[playerid] == 4)
					{
						PlayerInfo[playerid][pGender] = 1;
						SetTimerEx("TutorialDone", 1000, false, "i", playerid);
						SetPlayerSkin(playerid, 55);
						PlayerInfo[playerid][pSkin] = 55;
					}
        	    }
			}
		}
		case DIALOG_RACE:
  		{
           	switch(listitem)
        	{
          	  	case 0:
        	    {
					ShowPlayerDialog(playerid, DIALOG_GENDER, DIALOG_STYLE_LIST, "Gender", "Male\nFemale", "Choose", "Cancel");
					playerRace[playerid] = 1;
        	    }
         	  	case 1:
        	    {
  					ShowPlayerDialog(playerid, DIALOG_GENDER, DIALOG_STYLE_LIST, "Gender", "Male\nFemale", "Choose", "Cancel");
  					playerRace[playerid] = 2;
        	    }
        	    case 2:
        	    {
					ShowPlayerDialog(playerid, DIALOG_GENDER, DIALOG_STYLE_LIST, "Gender", "Male\nFemale", "Choose", "Cancel");
					playerRace[playerid] = 3;
        	    }
        	    case 3:
        	    {
					ShowPlayerDialog(playerid, DIALOG_GENDER, DIALOG_STYLE_LIST, "Gender", "Male\nFemale", "Choose", "Cancel");
					playerRace[playerid] = 4;
        	    }
			}
		}
		case DIALOG_AGE:
  		{
	        new age = strval(inputtext);
	        if(age < 8 || age > 65) return ShowPlayerDialog(playerid,DIALOG_AGE,DIALOG_STYLE_INPUT,"Age?","Please type in your characters age below. (7-100)","Submit","Cancel");
	        PlayerInfo[playerid][pAge]= age;
	        ShowPlayerDialog(playerid, DIALOG_RACE, DIALOG_STYLE_LIST, "Appearence", "Hispanic\nAfro-American\nCaucasian\nAsian", "Choose", "Cancel");
		}
		case DIALOG_DRUGS:
  		{
           	switch(listitem)
        	{
          	  	case 0:
        	    {
					if (PlayerInfo[playerid][dMarijuana] < 1) return SCM(playerid, COLOR_LIGHTRED, "[Error]: You do not have any marijuana.");
				    SetPlayerSpecialAction(playerid,SPECIAL_ACTION_SMOKE_CIGGY);
				    IsSmokingJoint[playerid] = 1;

				    SetTimerEx("MarijuanaEffect", 300000, 0, "i", playerid);


				    PlayerInfo[playerid][dMarijuana] -= 1;
				    PlayerActionMessage(playerid,15.0,"lights up a large spliff.");
        	    }
         	  	case 1:
        	    {
  	        		new
					Float: parmour;
    				if (PlayerInfo[playerid][dCocaine] < 1) return SCM(playerid, COLOR_LIGHTRED, "[Error]: You do not have any cocaine.");
    				if (parmour > 20) return SCM(playerid, COLOR_LIGHTRED, "[Error]: You can't do any more cocaine.");
    				if(IsCocaineHigh[playerid] == 1) return SCM(playerid, COLOR_LIGHTRED, "[Error]: You have to wait a while before taking more cocaine.");

					SetTimerEx("CocaineEffect", 300000, 0, "i", playerid);

				    PlayerInfo[playerid][dCocaine] -= 1;
				    IsCocaineHigh[playerid] = 1;
				    PlayerActionMessage(playerid,15.0,"sniffs some cocaine.");
        	    }
        	    case 2:
        	    {
   	        		new
					Float: parmour;
    				if (PlayerInfo[playerid][dLSD] < 1) return SCM(playerid, COLOR_LIGHTRED, "[Error]: You do not have any LSD.");
    				if (parmour > 20) return SCM(playerid, COLOR_LIGHTRED, "[Error]: You can't do any more LSD.");
    				if(IsLSDHigh[playerid] == 1) return SCM(playerid, COLOR_LIGHTRED, "[Error]: You have to wait a while before taking more LSD.");

    				SetTimerEx("LSDEffect", 300000, 0, "i", playerid);


				    PlayerInfo[playerid][dLSD] -= 1;
				    IsLSDHigh[playerid] = 1;
				    PlayerActionMessage(playerid,15.0,"places a LSD hit on his tounge.");
        	    }
			}
		}
		case 76:
  		{
           	switch(listitem)
        	{
        	    case 0:
        	    {

					new string[128], Float:BBCoord[4];
				    GetPlayerPos(playerid, BBCoord[0], BBCoord[1], BBCoord[2]);
				    GetPlayerFacingAngle(playerid, BBCoord[3]);
				    SetPVarFloat(playerid, "BBX", BBCoord[0]);
				    SetPVarFloat(playerid, "BBY", BBCoord[1]);
				    SetPVarFloat(playerid, "BBZ", BBCoord[2]);

				    BBCoord[0] += (2 * floatsin(-BBCoord[3], degrees));
				   	BBCoord[1] += (2 * floatcos(-BBCoord[3], degrees));
				   	BBCoord[2] -= 1.0;
					if(PlayerInfo[playerid][pBoombox] == 0) return SCM(playerid, COLOR_LIGHTRED, "[Error]: You do not have a boombox.");
					if(GetPVarInt(playerid, "PlacedBB")) return SCM(playerid, COLOR_LIGHTRED, "[Error]: You have already put down a boombox.");
					foreach(Player, i)
					{
				 		if(GetPVarType(i, "PlacedBB"))
				   		{
				  			if(IsPlayerInRangeOfPoint(playerid, 30.0, GetPVarFloat(i, "BBX"), GetPVarFloat(i, "BBY"), GetPVarFloat(i, "BBZ")))
							{
				   				SCM(playerid, COLOR_LIGHTRED, "[Error]: You can't put a boombox here. Someone is already listening to music here.");
							    return 1;
							}
						}
					}
				    PlayerActionMessage(playerid,20.0, "places a boombox on the ground.");

					SetPVarInt(playerid, "PlacedBB", CreateDynamicObject(2226, BBCoord[0], BBCoord[1], BBCoord[2], 0.0, 0.0, 0.0, .worldid = GetPlayerVirtualWorld(playerid), .interiorid = GetPlayerInterior(playerid)));
					format(string, sizeof(string), "Owner: %s", GetName(playerid));
					SetPVarInt(playerid, "BBLabel", _:CreateDynamic3DTextLabel(string, -1, BBCoord[0], BBCoord[1], BBCoord[2]+0.6, 5, .worldid = GetPlayerVirtualWorld(playerid), .interiorid = GetPlayerInterior(playerid)));
					SetPVarInt(playerid, "BBArea", CreateDynamicSphere(BBCoord[0], BBCoord[1], BBCoord[2], 30.0, GetPlayerVirtualWorld(playerid), GetPlayerInterior(playerid)));
					SetPVarInt(playerid, "BBInt", GetPlayerInterior(playerid));
					SetPVarInt(playerid, "BBVW", GetPlayerVirtualWorld(playerid));
					ApplyAnimation(playerid,"BOMBER","BOM_Plant",4.0,0,0,0,0,0,1);
        	    }
        	    case 1:
        	    {
					if(GetPVarType(playerid, "PlacedBB"))
					{
						if(IsPlayerInRangeOfPoint(playerid, 3.0, GetPVarFloat(playerid, "BBX"), GetPVarFloat(playerid, "BBY"), GetPVarFloat(playerid, "BBZ")))
						{
							ShowPlayerDialog(playerid,75,DIALOG_STYLE_LIST,"Radio List","Jazz\nPop\nHip-Hop\nR&B and Urban\nRock\nCountry\nEnter URL\nTurn Off Boombox","Select", "Cancel");
						}
						else
						{
   							return SCM(playerid, COLOR_LIGHTRED, "[Error]: You're not near your boombox.");
						}
		    			}
					    else
					    {
					        SCM(playerid, COLOR_LIGHTRED, "[Error]: You have not placed a boombox.");
						}
        	    }
        	    case 2:
        	    {
     				if(!GetPVarType(playerid, "PlacedBB"))
				    {
				        SCM(playerid, COLOR_LIGHTRED, "[Error]: You have not placed a boombox.");
				    }
					else if(IsPlayerInRangeOfPoint(playerid, 3.0, GetPVarFloat(playerid, "BBX"), GetPVarFloat(playerid, "BBY"), GetPVarFloat(playerid, "BBZ")))
				    {
				        PickUpBoombox(playerid);
				        PlayerActionMessage(playerid,20.0, "picks up a boombox from the ground.");
					}
        	    }
			}
		}
		case DIALOG_LOCKER:
  	    	 {
           	switch(listitem)
        	{
        	    case 0:
        	    {
					SCM(playerid, COLOR_LSPD, "[LAPD]: You've equipped yourself with armour.");
					SetPlayerArmour(playerid, 49);
        	    }
        	    case 1:
        	    {
					SCM(playerid, COLOR_LSPD, "[LAPD]: You've equipped yourself with a nightstick.");
					GivePlayerWeapon(playerid, 3, 1);
        	    }
        	    case 2:
        	    {
					SCM(playerid, COLOR_LSPD, "[LAPD]: You've equipped yourself with pepper-spray.");
					GivePlayerWeapon(playerid, 41, 9999999999);
        	    }
        	    case 3:
        	    {
					SCM(playerid, COLOR_LSPD, "[LAPD]: You've equipped yourself with a deagle.");
					GivePlayerWeapon(playerid, 24, 100);
        	    }
        	    case 4:
        	    {
					SCM(playerid, COLOR_LSPD, "[LAPD]: You've equipped yourself with a shotgun.");
					GivePlayerWeapon(playerid, 25, 25);
        	    }
         	   	case 5:
        	    {
					SCM(playerid, COLOR_LSPD, "[LAPD]: You've equipped yourself with a MP5.");
					GivePlayerWeapon(playerid, 29, 500);
        	    }
        	   	case 6:
        	    {
					SCM(playerid, COLOR_LSPD, "[LAPD]: You've equipped yourself with a M4.");
					GivePlayerWeapon(playerid, 31, 500);
        	    }
			}
		}
		case 10:// Our dialog!
	 	{
           	switch(listitem)// Checking which listitem was selected
        	{
        	    case 0:// The first item listed
        	    {
        	        if(GetPlayerCash(playerid) < 49) return SendClientMessage(playerid, COLOR_LIGHTRED, "[Error]: You don't have enough cash.");
        	        GivePlayerCash(playerid, -50);
        	        PlayerInfo[playerid][dMarijuana] += 10;
        	    }
        	    case 1: // The second item listed
        	    {
        	        if(GetPlayerCash(playerid) < 99) return SendClientMessage(playerid, COLOR_LIGHTRED, "[Error]: You don't have enough cash.");
        	        GivePlayerCash(playerid, -100);
					PlayerInfo[playerid][dCocaine] += 10;
        	    }
        	    case 2: // The third item listed
        	    {
        	        if(GetPlayerCash(playerid) < 99) return SendClientMessage(playerid, COLOR_LIGHTRED, "[Error]: You don't have enough cash.");
        	        GivePlayerCash(playerid, -100);
        	        PlayerInfo[playerid][dLSD] += 5;
 	   			}
        	}
    	}
		case 15:// Our dialog!
  		{
           	switch(listitem)// Checking which listitem was selected
        	{
        	    case 0:// The first item listed
        	    {
        	        if(GetPlayerCash(playerid) < 99) return SendClientMessage(playerid, COLOR_LIGHTRED, "[Error]: You don't have enough cash.");
        	        GivePlayerCash(playerid, -100);
        	        GivePlayerWeapon(playerid, 4, 1);
        	    }
        	    case 1: // The second item listed
        	    {
        	        if(GetPlayerCash(playerid) < 49) return SendClientMessage(playerid, COLOR_LIGHTRED, "[Error]: You don't have enough cash.");
        	        GivePlayerCash(playerid, -50);
        	        GivePlayerWeapon(playerid, 5, 1);
    	        	   }
    	    	   }
       		}
	//RASH
       /* case DIALOG_REGISTER:
		{
			if (!response) return Kick(playerid);
			
			if(response)
			{
				if(!strlen(inputtext)) return ShowPlayerDialog(playerid, DIALOG_REGISTER, DIALOG_STYLE_INPUT, "Register","You have entered an invalid password.\n""Type your password below to register a new account.","Register","Quit");
				new IP[22];
				GetPlayerIp(playerid, IP, sizeof(IP));
				new INI:File = INI_Open(UserPath(playerid));
				INI_SetTag(File,"data");
				INI_WriteInt(File,"Password",udb_hash(inputtext));
				INI_WriteInt(File,"Cash",0);
				INI_WriteInt(File,"Admin",0);
				INI_WriteInt(File,"Kills",0);
				INI_WriteInt(File,"Deaths",0);
				INI_WriteInt(File,"LSD",0);
				INI_WriteInt(File,"Cocaine",0);
				INI_WriteInt(File,"Marijuana",0);
				INI_WriteInt(File,"Respect",0);
				INI_WriteInt(File,"Cigarettes",0);
				INI_WriteInt(File,"Beer",0);
				INI_WriteString(File, "Ip", IP);
				INI_WriteFloat(File,"Health",0);
				INI_WriteInt(File,"BankAccount",0);
				INI_WriteInt(File,"Datasaved",0);
				INI_WriteInt(File,"Number",0);
				INI_WriteInt(File,"Level",0);
				INI_Close(File);
				FadeColorForPlayer(playerid,0,0,0,0,0,0,0,255,15,0);
				GivePlayerCash(playerid, 50);
				PlayerInfo[playerid][pSkin] = 26;
				PlayerInfo[playerid][pXPos] = 1743.0449;
				PlayerInfo[playerid][pYPos] = -1861.1635;
				PlayerInfo[playerid][pZPos] = 13.5779;
				PlayerInfo[playerid][pLevel] = 1;
				SetTimerEx("StartIntro", 1500, false, "i", playerid);
				new playerphone = 150000 + random(500000);//minimum 1000  max 9999 //giving one at the start
				PlayerInfo[playerid][pNumber] = playerphone;
			}*/
		case 1:
		{
			if(!strlen(inputtext)) 
				ShowPlayerDialog(playerid,1,1,"Регистрация на \"HARD CORE MOTHER FUCKER\"","Вы не ввели пароль!\nЧто-бы начать играть вам нужно:\n1.Зарегестрироваться;\n2.Заполнить анкету;\n3.Пройти обучение.\nЧто-бы зарегестрироваться,\nпожалуйте введите пароль ниже!\n\t\tMAMKY_EBAL.NET","Далее","");
			else 
				{
					mysql_real_escape_string(inputtext,PlayerInfo[playerid][pPass]);
					ShowPlayerDialog(playerid,2,0,"Выбор пола","Пожалуйста выберите пол,\nчто-бы продолжить регистрацию.\nВы мужчина или женщина?","Мужчина","Женщина");
				}
		}
		case 2:
		{
			new SeX[64];PlayerInfo[playerid][pMoney] = 2500; PlayerInfo[playerid][pLevel] = 1;GivePlayerMoney(playerid,PlayerInfo[playerid][pMoney]);SetPlayerScore(playerid,PlayerInfo[playerid][pLevel]);
			if(response == 1)
			{
				new RandomMale = random(sizeof(RandomMaleSkins));PlayerInfo[playerid][pSex] = 1;PlayerInfo[playerid][pSkin] = RandomMaleSkins[RandomMale][0];SetSpawnInfo(playerid,0,PlayerInfo[playerid][pSkin],2233.7,-1165.5,1030,180,0,0,0,0,0,0);SetPlayerInterior(playerid,15);SpawnPlayer(playerid);
			}
			else
			{
				new RandomFemale = random(sizeof(RandomFemaleSkins));PlayerInfo[playerid][pSex] = 2;SetPlayerSkin(playerid, RandomFemaleSkins[RandomFemale][0]);PlayerInfo[playerid][pSkin] = GetPlayerSkin(playerid);SetSpawnInfo(playerid,0,PlayerInfo[playerid][pSkin],2245,-1164,1030,0,0,0,0,0,0,0);SetPlayerInterior(playerid,15);SpawnPlayer(playerid);
			}
			if(PlayerInfo[playerid][pSex] == 1){SeX="Мужчина";}
			if(PlayerInfo[playerid][pSex] == 2){SeX="Женщина";}
			format(qwery,256,"Вы прошли все этапы регистрации!\nСпасибо за регистрацию.\nПриятной игры.\nВаше имя на сервере:%s,\nВаш пароль:%s,\nВаш пол:%s,\nВаша наличность:%d",PlayerInfo[playerid][pName],PlayerInfo[playerid][pPass],SeX,PlayerInfo[playerid][pMoney]);
			ShowPlayerDialog(playerid,3,0,"Конец регистрации",qwery,"Завершить","");
		}
		case 3:
			{
				pLogged[playerid] = 1;
				format(qwery,256,"INSERT INTO `playerinfo` (`name`,`password`,`sex`,`skin`,`money`,`lvl`,`adminlvl`,`team`,`rank`) VALUES ('%s','%s','%d','%d','%d','%d',0,0,0)",PlayerInfo[playerid][pName],PlayerInfo[playerid][pPass],PlayerInfo[playerid][pSex],PlayerInfo[playerid][pSkin],PlayerInfo[playerid][pMoney],PlayerInfo[playerid][pLevel]);
				mysql_query(qwery);
			}
		//RASH
        case DIALOG_LOGIN:
        {
            if ( !response ) return Kick ( playerid );
            if( response )
            {
                if(udb_hash(inputtext) == PlayerInfo[playerid][pPass])
                {
                    INI_ParseFile(UserPath(playerid), "LoadUser_%s", .bExtra = true, .extra = playerid);
                    GivePlayerCash(playerid, PlayerInfo[playerid][pCash]);
                    SetSpawnInfo(playerid, 0, 26, 1743.0449,-1861.1635,13.5779, 269.9902, 0, 0, 0, 0, 0, 0);
                    SpawnPlayer(playerid);
                    LoadFightingStyle(playerid);
                   	FadeColorForPlayer(playerid,0,0,0,255,0,0,0,0,15,0);
                    SCM(playerid, COLOR_GOLD, "* You have successfully logged in.");
                    SetPlayerScore(playerid, PlayerInfo[playerid][pLevel]);
                   	if(PlayerInfo[playerid][pBanned] == 1)
					{
    					Ban(playerid);
					}
                }
                else
                {
                    ShowPlayerDialog(playerid, DIALOG_LOGIN, DIALOG_STYLE_INPUT,"Login","You have entered an incorrect password.\n""Type your password below to login.","Login","Quit");
                }
                return 1;
            }
        }
    }
	if(dialogid == DIALOG_ERROR)
	{
		ShowDialog(playerid, DialogReturn[playerid]);
		return 1;
	}
	DialogReturn[playerid] = dialogid;
	if(dialogid == DIALOG_VEHICLE)
	{
		if(response)
		{
			switch(listitem)
			{
				case 0:
				{
					new vehicleid = GetPlayerVehicleID(playerid);
					GetVehicleParamsEx(vehicleid, engine, lights, alarm, doors, bonnet, boot, objective);
					if(engine == 0 && Fuel[vehicleid] <= 0)
					{
						ShowErrorDialog(playerid, "* This vehicle is out of fuel.");
						return 1;
					}
					if(engine == 1) { engine = 0; lights = 0; }
					else { engine = 1; lights = 1; }
					SetVehicleParamsEx(vehicleid, engine, lights, alarm, doors, bonnet, boot, objective);
				}
				case 1:
				{
					new vehicleid = GetPlayerVehicleID(playerid);
					GetVehicleParamsEx(vehicleid, engine, lights, alarm, doors, bonnet, boot, objective);
					if(lights == 1) lights = 0; else lights = 1;
					SetVehicleParamsEx(vehicleid, engine, lights, alarm, doors, bonnet, boot, objective);
				}
				case 2:
				{
					new vehicleid = GetPlayerVehicleID(playerid);
					GetVehicleParamsEx(vehicleid, engine, lights, alarm, doors, bonnet, boot, objective);
					if(bonnet == 1) bonnet = 0; else bonnet = 1;
					SetVehicleParamsEx(vehicleid, engine, lights, alarm, doors, bonnet, boot, objective);
				}
				case 3:
				{
					new vehicleid = GetPlayerVehicleID(playerid);
					GetVehicleParamsEx(vehicleid, engine, lights, alarm, doors, bonnet, boot, objective);
					if(boot == 1) boot = 0; else boot = 1;
					SetVehicleParamsEx(vehicleid, engine, lights, alarm, doors, bonnet, boot, objective);
				}
				case 4:
				{
					if(!GetPVarInt(playerid, "GasCan"))
					{
						ShowErrorDialog(playerid, "* You don't have a gas can.");
						return 1;
					}
					new vehicleid = GetPlayerVehicleID(playerid);
					if(Fuel[vehicleid] < 80.0) Fuel[vehicleid] += 20.0;
					else Fuel[vehicleid] = 100.0;
					SetPVarInt(playerid, "GasCan", 0);
					SendClientMessage(playerid, COLOR_GOLD, "You have filled the fuel tank with 20% fuel.");
				}
				case 5:
				{
					new id = GetPVarInt(playerid, "DialogValue1");
					if(GetPlayerVehicleAccess(playerid, id) < 2)
					{
						ShowErrorDialog(playerid, "You are not the owner of this vehicle.");
						return 1;
					}
					new msg[128];
					VehicleCreated[id] = 0;
					new money = VehicleValue[id]/2;
					GivePlayerCash(playerid, money);
					format(msg, sizeof(msg), "* You have sold your vehicle for $%d.", money);
					SendClientMessage(playerid, COLOR_GOLD, msg);
					RemovePlayerFromVehicle(playerid);
					DestroyVehicle(VehicleID[id]);
					SaveVehicle(id);
				}
				case 6:
				{
					new vehicleid = GetPVarInt(playerid, "DialogValue1");
					if(GetPlayerVehicleAccess(playerid, vehicleid) < 2)
					{
						ShowErrorDialog(playerid, "You are not the owner of this vehicle.");
						return 1;
					}
					GetVehiclePos(VehicleID[vehicleid], VehiclePos[vehicleid][0], VehiclePos[vehicleid][1], VehiclePos[vehicleid][2]);
					GetVehicleZAngle(VehicleID[vehicleid], VehiclePos[vehicleid][3]);
					VehicleInterior[vehicleid] = GetPlayerInterior(playerid);
					VehicleWorld[vehicleid] = GetPlayerVirtualWorld(playerid);
					if(GetPlayerCash(playerid) < 699) return SCM(playerid, COLOR_LIGHTRED, "* You don't have enough money. ($700)");
					GivePlayerCash(playerid, -700);
					SendClientMessage(playerid, COLOR_GOLD, "You have bought this parking spot for your vehicle.");
					UpdateVehicle(vehicleid, 1);
					PutPlayerInVehicle(playerid, VehicleID[vehicleid], 0);
					SaveVehicle(vehicleid);
				}
				case 7:
				{
					ShowDialog(playerid, DIALOG_VEHICLE_PLATE);
				}
			}
		}
		return 1;
	}
	if(dialogid == DIALOG_VEHICLE_BUY)
	{
		if(response)
		{
			if(GetPlayerVehicles(playerid) >= MAX_PLAYER_VEHICLES)
			{
				ShowErrorDialog(playerid, "You can't buy any more vehicles. Limit: " #MAX_PLAYER_VEHICLES );
				return 1;
			}
			new id = GetPVarInt(playerid, "DialogValue1");
			if(GetPlayerMoney(playerid) < VehicleValue[id])
			{
				ShowErrorDialog(playerid, "* You don't have enough money to buy this vehicle.");
				return 1;
			}
			new freeid = GetFreeVehicleID();
			if(!freeid)
			{
				ShowErrorDialog(playerid, "* Vehicle dealership is out of stock.");
				return 1;
			}
			GivePlayerCash(playerid, -VehicleValue[id]);
			new dealerid = strval(VehicleOwner[id]);
			VehicleCreated[freeid] = VEHICLE_PLAYER;
			VehicleModel[freeid] = VehicleModel[id];
			VehiclePos[freeid] = DealershipPos[dealerid];
			VehicleColor[freeid] = VehicleColor[id];
			VehicleInterior[freeid] = 0;
			VehicleWorld[freeid] = 0;
			VehicleValue[freeid] = VehicleValue[id];
			GetPlayerName(playerid, VehicleOwner[freeid], sizeof(VehicleOwner[]));
			VehicleNumberPlate[freeid] = DEFAULT_NUMBER_PLATE;
			for(new d=0; d < sizeof(VehicleTrunk[]); d++)
			{
				VehicleTrunk[freeid][d][0] = 0;
				VehicleTrunk[freeid][d][1] = 0;
			}
			for(new d=0; d < sizeof(VehicleMods[]); d++)
			{
				VehicleMods[freeid][d] = 0;
			}
			VehiclePaintjob[freeid] = 255;
			VehicleLock[freeid] = 0;
			VehicleAlarm[freeid] = 0;
			UpdateVehicle(freeid, 0);
			SaveVehicle(freeid);
			new msg[128];
			format(msg, sizeof(msg), "* You have bought this vehicle for $%d. Your vehicle is waiting for you outside.", VehicleValue[id]);
			SendClientMessage(playerid, COLOR_GOLD, msg);
		}
		else
		{
			new id = GetPVarInt(playerid, "DialogValue1");
			if(GetPlayerVehicleAccess(playerid, id) < 1)
			{
				RemovePlayerFromVehicle(playerid);
			}
		}
		return 1;
	}
	if(dialogid == DIALOG_VEHICLE_SELL)
	{
		if(response)
		{
			if(GetPlayerVehicles(playerid) >= MAX_PLAYER_VEHICLES)
			{
				ShowErrorDialog(playerid, "You can't buy any more vehicles. Limit: " #MAX_PLAYER_VEHICLES );
				return 1;
			}
			new targetid = GetPVarInt(playerid, "DialogValue1");
			new id = GetPVarInt(playerid, "DialogValue2");
			new price = GetPVarInt(playerid, "DialogValue3");
			if(GetPlayerMoney(playerid) < price)
			{
				ShowErrorDialog(playerid, "* You don't have enough money to buy this vehicle.");
				return 1;
			}
			new msg[128];
			GetPlayerName(playerid, VehicleOwner[id], sizeof(VehicleOwner[]));
			GivePlayerCash(playerid, -price);
			GivePlayerCash(targetid, price);
			SaveVehicle(id);
			format(msg, sizeof(msg), "* You have bought this vehicle for $%d.", price);
			SendClientMessage(playerid, COLOR_GOLD, msg);
			format(msg, sizeof(msg), "%s (%d) has accepted your offer and has bought the vehicle.", PlayerName(playerid), playerid);
			SendClientMessage(targetid, COLOR_GOLD, msg);
		}
		else
		{
			new targetid = GetPVarInt(playerid, "DialogValue1");
			new msg[128];
			format(msg, sizeof(msg), "%s (%d) denied your offer.", PlayerName(playerid), playerid);
			SendClientMessage(targetid, COLOR_GOLD, msg);
		}
		return 1;
	}
	if(dialogid == DIALOG_FINDVEHICLE)
	{
		if(response)
		{
			new id;
			sscanf(inputtext[4], "d", id);
			if(IsValidVehicle(id))
			{
				TrackCar[playerid] = VehicleID[id];
				SendClientMessage(playerid, COLOR_GOLD, "Your vehicle's location is shown on your minimap.");
			}
		}
		return 1;
	}
	if(dialogid == DIALOG_TRUNK)
	{
		if(response)
		{
			SetPVarInt(playerid, "DialogValue2", listitem);
			ShowDialog(playerid, DIALOG_TRUNK_ACTION);
		}
		else
		{
			new id = GetPVarInt(playerid, "DialogValue1");
			ToggleBoot(VehicleID[id], VEHICLE_PARAMS_OFF);
		}
		return 1;
	}
	if(dialogid == DIALOG_TRUNK_ACTION)
	{
		if(response)
		{
			new id = GetPVarInt(playerid, "DialogValue1");
			new slot = GetPVarInt(playerid, "DialogValue2");
			switch(listitem)
			{
			case 0:
			{
				new weaponid = GetPlayerWeapon(playerid);
				if(weaponid == 0)
				{
					ShowErrorDialog(playerid, "* You don't have a weapon in your hand.");
					return 1;
				}
				VehicleTrunk[id][slot][0] = weaponid;
				if(IsMeleeWeapon(weaponid)) VehicleTrunk[id][slot][1] = 1;
				else VehicleTrunk[id][slot][1] = GetPlayerAmmo(playerid);
				RemovePlayerWeapon(playerid, weaponid);
				SaveVehicle(id);
			}
			case 1:
			{
				if(VehicleTrunk[id][slot][1] <= 0)
				{
					ShowErrorDialog(playerid, "* This slot is empty.");
					return 1;
				}
				GivePlayerWeapon(playerid, VehicleTrunk[id][slot][0], VehicleTrunk[id][slot][1]);
				VehicleTrunk[id][slot][0] = 0;
				VehicleTrunk[id][slot][1] = 0;
				SaveVehicle(id);
			}
			}
		}
		ShowDialog(playerid, DIALOG_TRUNK);
		return 1;
	}
	if(dialogid == DIALOG_VEHICLE_PLATE)
	{
		if(response)
		{
			if(strlen(inputtext) < 1 || strlen(inputtext) >= sizeof(VehicleNumberPlate[]))
			{
				ShowErrorDialog(playerid, "* Invalid length.");
				return 1;
			}
			new id = GetPVarInt(playerid, "DialogValue1");
			new vehicleid = VehicleID[id];
			strmid(VehicleNumberPlate[id], inputtext, 0, sizeof(VehicleNumberPlate[]));
			SaveVehicle(id);
			SetVehicleNumberPlate(vehicleid, inputtext);
			SetVehicleToRespawn(vehicleid);
			new msg[128];
			format(msg, sizeof(msg), "You have changed vehicle number plate to %s.", inputtext);
			SendClientMessage(playerid, COLOR_GOLD, msg);
		}
		else ShowDialog(playerid, DIALOG_VEHICLE);
		return 1;
	}
	if(dialogid == DIALOG_FUEL)
	{
		if(response)
		{
			switch(listitem)
			{
			case 0:
			{
				if(GetPlayerState(playerid) != PLAYER_STATE_DRIVER)
				{
					ShowErrorDialog(playerid, "You are not driving a vehicle.");
					return 1;
				}
				new vehicleid = GetPlayerVehicleID(playerid);
				if(IsBicycle(vehicleid))
				{
					ShowErrorDialog(playerid, "Your vehicle doesn't have a fuel tank!");
					return 1;
				}
				if(Fuel[vehicleid] >= 100.0)
				{
					ShowErrorDialog(playerid, "Your vehicle fuel tank is full.");
					return 1;
				}
				if(GetPlayerMoney(playerid) < FUEL_PRICE)
				{
					ShowErrorDialog(playerid, "* You don't have enough money.");
					return 1;
				}
				RefuelTime[playerid] = 5;
				SetPVarFloat(playerid, "Fuel", Fuel[vehicleid]);
				GameTextForPlayer(playerid, "~g~refueling...", 2000, 3);
			}
			case 1:
			{
				if(GetPVarInt(playerid, "GasCan"))
				{
					ShowErrorDialog(playerid, "You already have a gas can.");
					return 1;
				}
				if(GetPlayerMoney(playerid) < GAS_CAN_PRICE)
				{
					ShowErrorDialog(playerid, "You don't have enough money.");
					return 1;
				}
				GivePlayerCash(playerid, -GAS_CAN_PRICE);
				SetPVarInt(playerid, "GasCan", 1);
				SendClientMessage(playerid, COLOR_GOLD, "You have bought a gas can for $" #GAS_CAN_PRICE );
			}
			}
		}
		return 1;
	}
	if(dialogid == DIALOG_EDITVEHICLE)
	{
		if(response)
		{
			new id = GetPVarInt(playerid, "DialogValue1");
			new nr, params[128];
			sscanf(inputtext, "ds", nr, params);
			switch(nr)
			{
			case 1:
			{
				new value = strval(params);
				if(value < 0) value = 0;
				VehicleValue[id] = value;
				UpdateVehicleLabel(id, 1);
				SaveVehicle(id);
				ShowDialog(playerid, DIALOG_EDITVEHICLE);
			}
			case 2:
			{
				new value;
				if(IsNumeric(params)) value = strval(params);
				else value = GetVehicleModelIDFromName(params);
				if(value < 400 || value > 611)
				{
					ShowErrorDialog(playerid, "Invalid vehicle model!");
					return 1;
				}
				VehicleModel[id] = value;
				for(new i=0; i < sizeof(VehicleMods[]); i++)
				{
					VehicleMods[id][i] = 0;
				}
				VehiclePaintjob[id] = 255;
				UpdateVehicle(id, 1);
				SaveVehicle(id);
				ShowDialog(playerid, DIALOG_EDITVEHICLE);
			}
			case 3:
			{
				new color1, color2;
				sscanf(params, "dd", color1, color2);
				VehicleColor[id][0] = color1;
				VehicleColor[id][1] = color2;
				SaveVehicle(id);
				ChangeVehicleColor(VehicleID[id], color1, color2);
				ShowDialog(playerid, DIALOG_EDITVEHICLE);
			}
			case 4:
			{
				if(strlen(params) < 1 || strlen(params) > 8)
				{
					ShowErrorDialog(playerid, "Invalid length!");
					return 1;
				}
				strmid(VehicleNumberPlate[id], params, 0, sizeof(params));
				SaveVehicle(id);
				SetVehicleNumberPlate(VehicleID[id], params);
				SetVehicleToRespawn(VehicleID[id]);
				ShowDialog(playerid, DIALOG_EDITVEHICLE);
			}
			case 5:
			{
				DestroyVehicle(VehicleID[id]);
				if(VehicleCreated[id] == VEHICLE_DEALERSHIP)
				{
					Delete3DTextLabel(VehicleLabel[id]);
				}
				VehicleCreated[id] = 0;
				SaveVehicle(id);
				new msg[128];
				format(msg, sizeof(msg), "You have deleted vehicle id %d", id);
				SendClientMessage(playerid, COLOR_WHITE, msg);
			}
			case 6:
			{
				if(GetPlayerState(playerid) != PLAYER_STATE_DRIVER)
				{
					ShowErrorDialog(playerid, "You are not driving the vehicle!");
					return 1;
				}
				GetVehiclePos(VehicleID[id], VehiclePos[id][0], VehiclePos[id][1], VehiclePos[id][2]);
				GetVehicleZAngle(VehicleID[id], VehiclePos[id][3]);
				VehicleInterior[id] = GetPlayerInterior(playerid);
				VehicleWorld[id] = GetPlayerVirtualWorld(playerid);
				SendClientMessage(playerid, COLOR_GOLD, "You have parked your vehicle at this position.");
				UpdateVehicle(id, 1);
				PutPlayerInVehicle(playerid, VehicleID[id], 0);
				SaveVehicle(id);
				ShowDialog(playerid, DIALOG_EDITVEHICLE);
			}
			case 7:
			{
				new Float:x, Float:y, Float:z;
				GetVehiclePos(VehicleID[id], x, y, z);
				SetPlayerPos(playerid, x, y, z+1);
				new msg[128];
				format(msg, sizeof(msg), "You have teleported to vehicle id %d", id);
				SendClientMessage(playerid, COLOR_WHITE, msg);
			}
			}
		}
		return 1;
	}
	return 0;
}


forward SaveBusiness(id);
public SaveBusiness(id)
{
    new file4[40];
    format(file4, sizeof(file4), BPATH, id);
    new INI:File = INI_Open(file4);
    INI_SetTag(File,"data");
    INI_WriteInt(File,"bOwned", BusinessInfo[id][bOwned]);
    INI_WriteInt(File,"bPrice", BusinessInfo[id][bPrice]);
    INI_WriteString(File,"bOwner", BusinessInfo[id][bOwner]);
    INI_WriteInt(File,"bType", BusinessInfo[id][bType]);
    INI_WriteInt(File,"bLocked", BusinessInfo[id][bLocked]);
    INI_WriteInt(File,"bMoney", BusinessInfo[id][bMoney]);
    INI_WriteFloat(File,"bEntranceX", BusinessInfo[id][bEntranceX]);
    INI_WriteFloat(File,"bEntranceY", BusinessInfo[id][bEntranceY]);
    INI_WriteFloat(File,"bEntranceZ", BusinessInfo[id][bEntranceZ]);
    INI_WriteFloat(File,"bEntranceA", BusinessInfo[id][bEntranceA]);
    INI_WriteFloat(File,"bExitX", BusinessInfo[id][bExitX]);
    INI_WriteFloat(File,"bExitY", BusinessInfo[id][bExitY]);
    INI_WriteFloat(File,"bExitZ", BusinessInfo[id][bExitZ]);
    INI_WriteFloat(File,"bExitA", BusinessInfo[id][bExitA]);
    INI_WriteInt(File,"bInt", BusinessInfo[id][bInt]);
    INI_WriteInt(File,"bWorld", BusinessInfo[id][bWorld]);
    INI_WriteInt(File,"bInsideInt", BusinessInfo[id][bInsideInt]);
    INI_WriteInt(File,"bInsideWorld", BusinessInfo[id][bInsideWorld]);
    INI_WriteString(File,"bName", BusinessInfo[id][bName]);
    INI_Close(File);
    return 1;
}

stock GetName(playerid)
{
    new
        name[24];
    GetPlayerName(playerid, name, sizeof(name));
    strreplace(name, '_', ' ');
    return name;
}

public ProxDetector(Float:radi, playerid, string[],col1,col2,col3,col4,col5)
{
	if(IsPlayerConnected(playerid))
	{
		new Float:posx, Float:posy, Float:posz;
		new Float:oldposx, Float:oldposy, Float:oldposz;
		new Float:tempposx, Float:tempposy, Float:tempposz;

		GetPlayerPos(playerid, oldposx, oldposy, oldposz);
		//radi = 2.0; //Trigger Radius
		for(new i = 0; i < MAX_PLAYERS; i++)
		{
			if(IsPlayerConnected(i))
			{
				if(!BigEar[i])
				{
					GetPlayerPos(i, posx, posy, posz);
					tempposx = (oldposx -posx);
					tempposy = (oldposy -posy);
					tempposz = (oldposz -posz);
					//printf("DEBUG: X:%f Y:%f Z:%f",posx,posy,posz);
					if (((tempposx < radi/16) && (tempposx > -radi/16)) && ((tempposy < radi/16) && (tempposy > -radi/16)) && ((tempposz < radi/16) && (tempposz > -radi/16)))
					{
					    if(GetPlayerVirtualWorld(i) == GetPlayerVirtualWorld(playerid))
					    {
							SendClientMessage(i, col1, string);
						}
					}
					else if (((tempposx < radi/8) && (tempposx > -radi/8)) && ((tempposy < radi/8) && (tempposy > -radi/8)) && ((tempposz < radi/8) && (tempposz > -radi/8)))
					{
                        if(GetPlayerVirtualWorld(i) == GetPlayerVirtualWorld(playerid))
                        {
							SendClientMessage(i, col2, string);
						}
					}
					else if (((tempposx < radi/4) && (tempposx > -radi/4)) && ((tempposy < radi/4) && (tempposy > -radi/4)) && ((tempposz < radi/4) && (tempposz > -radi/4)))
					{
					    if(GetPlayerVirtualWorld(i) == GetPlayerVirtualWorld(playerid))
					    {
							SendClientMessage(i, col3, string);
						}
					}
					else if (((tempposx < radi/2) && (tempposx > -radi/2)) && ((tempposy < radi/2) && (tempposy > -radi/2)) && ((tempposz < radi/2) && (tempposz > -radi/2)))
					{
					    if(GetPlayerVirtualWorld(i) == GetPlayerVirtualWorld(playerid))
					    {
							SendClientMessage(i, col4, string);
						}
					}
					else if (((tempposx < radi) && (tempposx > -radi)) && ((tempposy < radi) && (tempposy > -radi)) && ((tempposz < radi) && (tempposz > -radi)))
					{
                        if(GetPlayerVirtualWorld(i) == GetPlayerVirtualWorld(playerid))
                        {
							SendClientMessage(i, col5, string);
						}
					}
    	}
				else
				{
					SendClientMessage(i, col1, string);
				}
			}
		}
	}//not connected
	return 1;
}

stock strreplace(string[], find, replace)
{
    for(new i=0; string[i]; i++)
    {
        if(string[i] == find)
        {
            string[i] = replace;
        }
    }
}

public OnPlayerEnterCheckpoint(playerid)
{

	if(CP[playerid] == 69)
	{
		DisablePlayerCheckpoint(playerid);
		PlayerPlaySound(playerid, 1085,0.0,0.0,0.0);
	}
	if(DMVcp[playerid] == 1)
	{
		SetPlayerCheckpoint(playerid, 1964.1757,-1921.5619,13.2578, 3.0);
		PlayerPlaySound(playerid, 1085,0.0,0.0,0.0);
		DMVcp[playerid] = 2;
	}
	else if(DMVcp[playerid] == 2)
	{
	    SetPlayerCheckpoint(playerid, 1964.0962,-1763.8975,13.2577, 3.0);
	    PlayerPlaySound(playerid, 1085,0.0,0.0,0.0);
		DMVcp[playerid] = 3;
	}
	else if(DMVcp[playerid] == 3)
	{
	    SetPlayerCheckpoint(playerid, 2004.7006,-1741.5475,13.2578, 3.0);
	    PlayerPlaySound(playerid, 1085,0.0,0.0,0.0);
		DMVcp[playerid] = 4;
	}
	else if(DMVcp[playerid] == 4)
	{
	    SetPlayerCheckpoint(playerid, 2019.7920,-1674.7982,13.2578, 3.0);
	    PlayerPlaySound(playerid, 1085,0.0,0.0,0.0);
		DMVcp[playerid] = 5;
	}
	else if(DMVcp[playerid] == 5)
	{
	    SetPlayerCheckpoint(playerid, 2079.3333,-1739.0278,13.2593, 3.0);
	    PlayerPlaySound(playerid, 1085,0.0,0.0,0.0);
		DMVcp[playerid] = 6;
	}
	else if(DMVcp[playerid] == 6)
	{
	    SetPlayerCheckpoint(playerid, 2126.5793,-1755.2256,13.2810, 3.0);
	    PlayerPlaySound(playerid, 1085,0.0,0.0,0.0);
		DMVcp[playerid] = 7;
	}
	else if(DMVcp[playerid] == 7)
	{
	    SetPlayerCheckpoint(playerid, 2199.4177,-1735.9177,13.2740, 3.0);
	    PlayerPlaySound(playerid, 1085,0.0,0.0,0.0);
		DMVcp[playerid] = 8;
	}
	else if(DMVcp[playerid] == 8)
	{
	    SetPlayerCheckpoint(playerid, 2306.4548,-1735.0432,13.2595, 3.0);
	    PlayerPlaySound(playerid, 1085,0.0,0.0,0.0);
		DMVcp[playerid] = 9;
	}
	else if(DMVcp[playerid] == 9)
	{
	    SetPlayerCheckpoint(playerid, 2345.2490,-1672.6071,13.2305, 3.0);
	    PlayerPlaySound(playerid, 1085,0.0,0.0,0.0);
		DMVcp[playerid] = 10;
	}
	else if(DMVcp[playerid] == 10)
	{
	    SetPlayerCheckpoint(playerid, 2228.1807,-1648.6830,15.1874, 3.0);
	    PlayerPlaySound(playerid, 1085,0.0,0.0,0.0);
		DMVcp[playerid] = 11;
	}
	else if(DMVcp[playerid] == 11)
	{
	    SetPlayerCheckpoint(playerid, 2079.1394,-1628.0896,13.2578, 3.0);
	    PlayerPlaySound(playerid, 1085,0.0,0.0,0.0);
		DMVcp[playerid] = 12;
	}
	else if(DMVcp[playerid] == 12)
	{
	    SetPlayerCheckpoint(playerid, 2081.9314,-1780.0300,13.2577, 3.0);
	    PlayerPlaySound(playerid, 1085,0.0,0.0,0.0);
		DMVcp[playerid] = 13;
	}
	else if(DMVcp[playerid] == 13)
	{
 		SetPlayerCheckpoint(playerid, 2072.0359,-1907.9246,13.4226, 3.0);
 		PlayerPlaySound(playerid, 1085,0.0,0.0,0.0);
	    DMVcp[playerid] = 14;
	}
	else if(DMVcp[playerid] == 14)
	{
		new vehicle;
		vehicle = GetPlayerVehicleID(playerid);
		SetVehicleToRespawn(vehicle);
		DisablePlayerCheckpoint(playerid);
		PlayerPlaySound(playerid, 1085,0.0,0.0,0.0);
		PlayerInfo[playerid][pDriverLicense] = 1;
		DMVcp[playerid] = 0;
		SCM(playerid, COLOR_GREEN, "* Congratulations, you have passed the test and you now have a drivers license!");
	}
 	return 1;
}

public OnPlayerInteriorChange(playerid, newinteriorid, oldinteriorid)//This is called when a player's interior is changed.
{
    if(IsBeingSpeced[playerid] == 1)//If the player being spectated, changes an interior, then update the interior and virtualword for the spectator.
    {
        foreach(Player,i)
        {
            if(spectatorid[i] == playerid)
            {
                SetPlayerInterior(i,GetPlayerInterior(playerid));
                SetPlayerVirtualWorld(i,GetPlayerVirtualWorld(playerid));
            }
        }
    }
    return 1;
}

public UnJail(playerid)
{
	SetPlayerPos(playerid, 1555.5061,-1675.7239,16.1953);
	SetPlayerVirtualWorld(playerid, 0);
	
	SetPlayerInterior(playerid, 0);
	SCM(playerid, COLOR_LSPD, "* You have been released from prison. Try to be a better citizen in the future.");
	PlayerInfo[playerid][pInJailTime] = 0;
	PlayerInfo[playerid][pInJail] = 0;
}

public GiveRespectAgain(playerid)
{
	Respect[playerid] = 0;
}

public PoliceBroadcast(color,const string[],level)
{
	for(new i = 0; i < MAX_PLAYERS; i++)
	{
		if(IsPlayerConnected(i))
		{
			if(IsACop(i))
			{
				SendClientMessage(i, color, string);
			}
		}
	}
	return 1;
}

public ABroadCast(color,const string[],level)
{
	for(new i = 0; i < MAX_PLAYERS; i++)
	{
		if(IsPlayerConnected(i))
		{
			if (PlayerInfo[i][pAdmin] >= level)
			{
				SendClientMessage(i, color, string);
			}
		}
	}
	return 1;
}

stock IsACop(playerid)
{
    new bool:thing;
    switch(GetPlayerSkin(playerid))
    {
        case 280..288: thing = true;
        case 165, 166: thing = true;
        default: thing = false;
    }
    return thing;
}

forward UnsetKick(playerid);
public UnsetKick(playerid)
{
    Kick(playerid);
    return 1;
}

forward UnsetBan(playerid);
public UnsetBan(playerid)
{
    Ban(playerid);
    return 1;
}

stock GivePlayerCash(playerid, money)
{
    Cash[playerid] += money;
    ResetMoneyBar(playerid);//Resets the money in the original moneybar, Do not remove!
    UpdateMoneyBar(playerid,Cash[playerid]);//Sets the money in the moneybar to the serverside cash, Do not remove!
    return Cash[playerid];
}
stock SetPlayerCash(playerid, money)
{
    Cash[playerid] = money;
    ResetMoneyBar(playerid);//Resets the money in the original moneybar, Do not remove!
    UpdateMoneyBar(playerid,Cash[playerid]);//Sets the money in the moneybar to the serverside cash, Do not remove!
    return Cash[playerid];
}
stock ResetPlayerCash(playerid)
{
    Cash[playerid] = 0;
    ResetMoneyBar(playerid);//Resets the money in the original moneybar, Do not remove!
    UpdateMoneyBar(playerid,Cash[playerid]);//Sets the money in the moneybar to the serverside cash, Do not remove!
    return Cash[playerid];
}
stock GetPlayerCash(playerid)
{
    return Cash[playerid];
}

forward MoneyTimer();
public MoneyTimer()
{
    new username[MAX_PLAYER_NAME];
    for(new i=0; i<MAX_PLAYERS; i++)
    {
        if(IsPlayerConnected(i))
        {
            if(GetPlayerCash(i) != GetPlayerMoney(i))
            {
                ResetMoneyBar(i);//Resets the money in the original moneybar, Do not remove!
                UpdateMoneyBar(i,GetPlayerCash(i));//Sets the money in the moneybar to the serverside cash, Do not remove!
                new hack = GetPlayerMoney(i) - GetPlayerCash(i);
                GetPlayerName(i,username,sizeof(username));
                printf("%s has attempted to spawn $%d.", username,hack);
            }
        }
    }
}

public OnPlayerEnterDynamicArea(playerid, areaid)
{
	foreach(Player, i)
	{
	    if(GetPVarType(i, "BBArea"))
	    {
	        if(areaid == GetPVarInt(i, "BBArea"))
	        {
	            new station[256];
	            GetPVarString(i, "BBStation", station, sizeof(station));
	            if(!isnull(station))
				{
					PlayStream(playerid, station, GetPVarFloat(i, "BBX"), GetPVarFloat(i, "BBY"), GetPVarFloat(i, "BBZ"), 30.0, 1);
	            }
				return 1;
	        }
	    }
	}
	return 1;
}

public OnPlayerLeaveDynamicArea(playerid, areaid)
{
    foreach(Player, i)
	{
	    if(GetPVarType(i, "BBArea"))
	    {
	        if(areaid == GetPVarInt(i, "BBArea"))
	        {
	            StopStream(playerid);
				return 1;
	        }
	    }
	}
	return 1;
}

public OnPlayerUpdate(playerid)
{
	return 1;
}

public OnVehicleSpawn(vehicleid)
{
	SetVehicleParamsEx(vehicleid, 0, 0, alarm, 0, bonnet, boot, 0);
	VehicleSecurity[vehicleid] = 0;
	new id = GetVehicleID(vehicleid);
	if(IsValidVehicle(id))
	{
		if(VehicleColor[id][0] >= 0 && VehicleColor[id][1] >= 0)
			ChangeVehicleColor(vehicleid, VehicleColor[id][0], VehicleColor[id][1]);
		LinkVehicleToInterior(vehicleid, VehicleInterior[id]);
		SetVehicleVirtualWorld(vehicleid, VehicleWorld[id]);
		for(new i=0; i < sizeof(VehicleMods[]); i++)
		{
			AddVehicleComponent(vehicleid, VehicleMods[id][i]);
		}
		ChangeVehiclePaintjob(vehicleid, VehiclePaintjob[id]);
		if(VehicleLock[id]) ToggleDoors(vehicleid, VEHICLE_PARAMS_ON);
		if(VehicleAlarm[id]) VehicleSecurity[vehicleid] = 1;
	}
	return 1;
}

stock StopStream(playerid)
{
	DeletePVar(playerid, "pAudioStream");
    StopAudioStreamForPlayer(playerid);
}

stock PlayStream(playerid, url[], Float:posX = 0.0, Float:posY = 0.0, Float:posZ = 0.0, Float:distance = 50.0, usepos = 0)
{
	if(GetPVarType(playerid, "pAudioStream")) StopAudioStreamForPlayer(playerid);
	else SetPVarInt(playerid, "pAudioStream", 1);
    PlayAudioStreamForPlayer(playerid, url, posX, posY, posZ, distance, usepos);
}

stock PickUpBoombox(playerid)
{
    foreach(Player, i)
	{
 		if(IsPlayerInDynamicArea(i, GetPVarInt(playerid, "BBArea")))
   		{
     		StopStream(i);
		}
	}
	DeletePVar(playerid, "BBArea");
	DestroyDynamicObject(GetPVarInt(playerid, "PlacedBB"));
	DestroyDynamic3DTextLabel(Text3D:GetPVarInt(playerid, "BBLabel"));
	DeletePVar(playerid, "PlacedBB"); DeletePVar(playerid, "BBLabel");
 	DeletePVar(playerid, "BBX"); DeletePVar(playerid, "BBY"); DeletePVar(playerid, "BBZ");
	DeletePVar(playerid, "BBInt");
	DeletePVar(playerid, "BBVW");
	DeletePVar(playerid, "BBStation");
	return 1;
}

stock UserPath(playerid)
{
    new string[128],playername[MAX_PLAYER_NAME];
    GetPlayerName(playerid,playername,sizeof(playername));
    format(string,sizeof(string),PATH,playername);
    return string;
}

stock udb_hash(buf[]) {
    new length=strlen(buf);
    new s1 = 1;
    new s2 = 0;
    new n;
    for (n=0; n<length; n++)
    {
       s1 = (s1 + buf[n]) % 65521;
       s2 = (s2 + s1)     % 65521;
    }
    return (s2 << 16) + s1;
}

stock SendNearbyMessage(playerid, Float:radius, string[], col1, col2, col3, col4, col5)
{
	new Float:x, Float:y, Float:z;
	GetPlayerPos(playerid, x, y, z);
	new Float:ix, Float:iy, Float:iz;
	new Float:cx, Float:cy, Float:cz;
	foreach(Player, i)
	{
 		if(gPlayerLoggin{i})
	    {
	        if(GetPlayerInterior(playerid) == GetPlayerInterior(i) && GetPlayerVirtualWorld(playerid) == GetPlayerVirtualWorld(i))
	        {
				GetPlayerPos(i, ix, iy, iz);
				cx = (x - ix);
				cy = (y - iy);
				cz = (z - iz);
				if(((cx < radius/16) && (cx > -radius/16)) && ((cy < radius/16) && (cy > -radius/16)) && ((cz < radius/16) && (cz > -radius/16)))
				{
				    SCM(i, col1, string);
				}
				else if(((cx < radius/8) && (cx > -radius/8)) && ((cy < radius/8) && (cy > -radius/8)) && ((cz < radius/8) && (cz > -radius/8)))
				{
				    SCM(i, col2, string);
				}
				else if(((cx < radius/4) && (cx > -radius/4)) && ((cy < radius/4) && (cy > -radius/4)) && ((cz < radius/4) && (cz > -radius/4)))
				{
				    SCM(i, col3, string);
				}
				else if(((cx < radius/2) && (cx > -radius/2)) && ((cy < radius/2) && (cy > -radius/2)) && ((cz < radius/2) && (cz > -radius/2)))
				{
				    SCM(i, col4, string);
				}
				else if(((cx < radius) && (cx > -radius)) && ((cy < radius) && (cy > -radius)) && ((cz < radius) && (cz > -radius)))
				{
				    SCM(i, col5, string);
				}
			}
	    }
	}
	return 1;
}

public Payday(playerid)
{
	new
	string[50];
	
	PlayerInfo[playerid][pExperience] += 1;
	if(PlayerInfo[playerid][pExperience] == 8)
	{
 		SCM(playerid, -1, "___________________[PAYDAY INFORMATION]___________________");
        format(string,sizeof(string), "New bank balance: $%d", PlayerInfo[playerid][pBankAccount]);
        SCM(playerid, COLOR_WHITE, string);

	    SCM(playerid, -1, "* You have leveled up to level 2.");
	    PlayerInfo[playerid][pLevel] = 2;
     	SetPlayerScore(playerid, PlayerInfo[playerid][pLevel]);
		format(string, sizeof(string), "~w~PayDay! ~n~~g~$%d", 200);
		GameTextForPlayer(playerid, string, 3000, 1);
	}
	if(PlayerInfo[playerid][pExperience] == 16)
	{
 		SCM(playerid, -1, "___________________[PAYDAY INFORMATION]___________________");
        format(string,sizeof(string), "New bank balance: $%d", PlayerInfo[playerid][pBankAccount]);
        SCM(playerid, COLOR_WHITE, string);

	    SCM(playerid, -1, "* You have leveled up to level 3.");
	    PlayerInfo[playerid][pLevel] = 3;
     	SetPlayerScore(playerid, PlayerInfo[playerid][pLevel]);
		format(string, sizeof(string), "~w~PayDay! ~n~~g~$%d", 200);
		GameTextForPlayer(playerid, string, 3000, 1);
	}
	if(PlayerInfo[playerid][pExperience] == 24)
	{
 		SCM(playerid, -1, "___________________[PAYDAY INFORMATION]___________________");
        format(string,sizeof(string), "New bank balance: $%d", PlayerInfo[playerid][pBankAccount]);
        SCM(playerid, COLOR_WHITE, string);
	    PlayerInfo[playerid][pLevel] = 4;
     	SetPlayerScore(playerid, PlayerInfo[playerid][pLevel]);
	    SCM(playerid, -1, "* You have leveled up to level 4.");
		format(string, sizeof(string), "~w~PayDay! ~n~~g~$%d", 200);
		GameTextForPlayer(playerid, string, 3000, 1);
	}
	if(PlayerInfo[playerid][pExperience] == 32)
	{
 		SCM(playerid, -1, "___________________[PAYDAY INFORMATION]___________________");
        format(string,sizeof(string), "New bank balance: $%d", PlayerInfo[playerid][pBankAccount]);
        SCM(playerid, COLOR_WHITE, string);
	    PlayerInfo[playerid][pLevel] = 5;
     	SetPlayerScore(playerid, PlayerInfo[playerid][pLevel]);
	    SCM(playerid, -1, "* You have leveled up to level 5.");
		format(string, sizeof(string), "~w~PayDay! ~n~~g~$%d", 200);
		GameTextForPlayer(playerid, string, 3000, 1);
	}
	if(PlayerInfo[playerid][pExperience] == 40)
	{
 		SCM(playerid, -1, "___________________[PAYDAY INFORMATION]___________________");
        format(string,sizeof(string), "New bank balance: $%d", PlayerInfo[playerid][pBankAccount]);
        SCM(playerid, COLOR_WHITE, string);
	    PlayerInfo[playerid][pLevel] = 6;
     	SetPlayerScore(playerid, PlayerInfo[playerid][pLevel]);
	    SCM(playerid, -1, "* You have leveled up to level 6.");
		format(string, sizeof(string), "~w~PayDay! ~n~~g~$%d", 200);
		GameTextForPlayer(playerid, string, 3000, 1);
	}
	if(PlayerInfo[playerid][pExperience] == 48)
	{
 		SCM(playerid, -1, "___________________[PAYDAY INFORMATION]___________________");
        format(string,sizeof(string), "New bank balance: $%d", PlayerInfo[playerid][pBankAccount]);
        SCM(playerid, COLOR_WHITE, string);
	    PlayerInfo[playerid][pLevel] = 7;
     	SetPlayerScore(playerid, PlayerInfo[playerid][pLevel]);
	    SCM(playerid, -1, "* You have leveled up to level 7.");
		format(string, sizeof(string), "~w~PayDay! ~n~~g~$%d", 200);
		GameTextForPlayer(playerid, string, 3000, 1);
	}
	if(PlayerInfo[playerid][pExperience] == 56)
	{
 		SCM(playerid, -1, "___________________[PAYDAY INFORMATION]___________________");
        format(string,sizeof(string), "New bank balance: $%d", PlayerInfo[playerid][pBankAccount]);
        SCM(playerid, COLOR_WHITE, string);
	    PlayerInfo[playerid][pLevel] = 8;
     	SetPlayerScore(playerid, PlayerInfo[playerid][pLevel]);
	    SCM(playerid, -1, "* You have leveled up to level 8.");
		format(string, sizeof(string), "~w~PayDay! ~n~~g~$%d", 200);
		GameTextForPlayer(playerid, string, 3000, 1);
	}
	if(PlayerInfo[playerid][pExperience] == 64)
	{
 		SCM(playerid, -1, "___________________[PAYDAY INFORMATION]___________________");
        format(string,sizeof(string), "New bank balance: $%d", PlayerInfo[playerid][pBankAccount]);
        SCM(playerid, COLOR_WHITE, string);
	    PlayerInfo[playerid][pLevel] = 9;
     	SetPlayerScore(playerid, PlayerInfo[playerid][pLevel]);
	    SCM(playerid, -1, "* You have leveled up to level 9.");
		format(string, sizeof(string), "~w~PayDay! ~n~~g~$%d", 200);
		GameTextForPlayer(playerid, string, 3000, 1);
	}
	if(PlayerInfo[playerid][pExperience] == 72)
	{
 		SCM(playerid, -1, "___________________[PAYDAY INFORMATION]___________________");
        format(string,sizeof(string), "New bank balance: $%d", PlayerInfo[playerid][pBankAccount]);
        SCM(playerid, COLOR_WHITE, string);
	    PlayerInfo[playerid][pLevel] = 10;
     	SetPlayerScore(playerid, PlayerInfo[playerid][pLevel]);
	    SCM(playerid, -1, "* You have leveled up to level 10.");
		format(string, sizeof(string), "~w~PayDay! ~n~~g~$%d", 200);
		GameTextForPlayer(playerid, string, 3000, 1);
	}
	if(PlayerInfo[playerid][pExperience] == 80)
	{
 		SCM(playerid, -1, "___________________[PAYDAY INFORMATION]___________________");
        format(string,sizeof(string), "New bank balance: $%d", PlayerInfo[playerid][pBankAccount]);
        SCM(playerid, COLOR_WHITE, string);
	    PlayerInfo[playerid][pLevel] = 11;
     	SetPlayerScore(playerid, PlayerInfo[playerid][pLevel]);
	    SCM(playerid, -1, "* You have leveled up to level 11.");
		format(string, sizeof(string), "~w~PayDay! ~n~~g~$%d", 200);
		GameTextForPlayer(playerid, string, 3000, 1);
	}
	if(PlayerInfo[playerid][pExperience] == 88)
 	{
 		SCM(playerid, -1, "___________________[PAYDAY INFORMATION]___________________");
        format(string,sizeof(string), "New bank balance: $%d", PlayerInfo[playerid][pBankAccount]);
        SCM(playerid, COLOR_WHITE, string);
	    PlayerInfo[playerid][pLevel] = 12;
     	SetPlayerScore(playerid, PlayerInfo[playerid][pLevel]);
	    SCM(playerid, -1, "* You have leveled up to level 12.");
		format(string, sizeof(string), "~w~PayDay! ~n~~g~$%d", 200);
		GameTextForPlayer(playerid, string, 3000, 1);
	}
	if(PlayerInfo[playerid][pExperience] == 96)
 	{
 		SCM(playerid, -1, "___________________[PAYDAY INFORMATION]___________________");
        format(string,sizeof(string), "New bank balance: $%d", PlayerInfo[playerid][pBankAccount]);
        SCM(playerid, COLOR_WHITE, string);
	    PlayerInfo[playerid][pLevel] = 13;
     	SetPlayerScore(playerid, PlayerInfo[playerid][pLevel]);
	    SCM(playerid, -1, "* You have leveled up to level 13.");
		format(string, sizeof(string), "~w~PayDay! ~n~~g~$%d", 200);
		GameTextForPlayer(playerid, string, 3000, 1);
	}
	if(PlayerInfo[playerid][pExperience] == 103)
 	{
 		SCM(playerid, -1, "___________________[PAYDAY INFORMATION]___________________");
        format(string,sizeof(string), "New bank balance: $%d", PlayerInfo[playerid][pBankAccount]);
        SCM(playerid, COLOR_WHITE, string);
	    PlayerInfo[playerid][pLevel] = 14;
     	SetPlayerScore(playerid, PlayerInfo[playerid][pLevel]);
	    SCM(playerid, -1, "* You have leveled up to level 14.");
		format(string, sizeof(string), "~w~PayDay! ~n~~g~$%d", 200);
		GameTextForPlayer(playerid, string, 3000, 1);
	}
	if(PlayerInfo[playerid][pExperience] == 111)
 	{
 		SCM(playerid, -1, "___________________[PAYDAY INFORMATION]___________________");
        format(string,sizeof(string), "New bank balance: $%d", PlayerInfo[playerid][pBankAccount]);
        SCM(playerid, COLOR_WHITE, string);
	    PlayerInfo[playerid][pLevel] = 15;
     	SetPlayerScore(playerid, PlayerInfo[playerid][pLevel]);
	    SCM(playerid, -1, "* You have leveled up to level 15.");
		format(string, sizeof(string), "~w~PayDay! ~n~~g~$%d", 200);
		GameTextForPlayer(playerid, string, 3000, 1);
	}
	if(PlayerInfo[playerid][pLevel] < 2)
	{
	    SCM(playerid, -1, "___________________[PAYDAY INFORMATION]___________________");
     	PlayerInfo[playerid][pBankAccount] += 200; // Under LVL 2 bonus
        format(string,sizeof(string), "New bank balance: $%d", PlayerInfo[playerid][pBankAccount]);
        SCM(playerid, COLOR_WHITE, string);

	    SCM(playerid, -1, "* You have received a bonus of $200 due to being under level 2.");
		format(string, sizeof(string), "~w~PayDay! ~n~~g~$%d", 200);
		GameTextForPlayer(playerid, string, 3000, 1);
	}
	else if(PlayerInfo[playerid][pLevel] < 3)
	{
	    SCM(playerid, -1, "___________________[PAYDAY INFORMATION]___________________");
     	PlayerInfo[playerid][pBankAccount] += 100; // Under LVL 3 bonus
        format(string,sizeof(string), "New bank balance: $%d", PlayerInfo[playerid][pBankAccount]);
        SCM(playerid, COLOR_WHITE, string);

	    SCM(playerid, -1, "* You have received a bonus of $100 due to being under level 3.");
		format(string, sizeof(string), "~w~PayDay! ~n~~g~$%d", 200);
		GameTextForPlayer(playerid, string, 3000, 1);
	}
	else if(PlayerInfo[playerid][pLevel] < 4)
	{
	    SCM(playerid, -1, "___________________[PAYDAY INFORMATION]___________________");
     	PlayerInfo[playerid][pBankAccount] += 50; // Under LVL 4 bonus
        format(string,sizeof(string), "New bank balance: $%d", PlayerInfo[playerid][pBankAccount]);
        SCM(playerid, COLOR_WHITE, string);

	    SCM(playerid, -1, "* You have received a bonus of $50 due to being under level 4.");
		format(string, sizeof(string), "~w~PayDay! ~n~~g~$%d", 200);
		GameTextForPlayer(playerid, string, 3000, 1);
	}
}

stock BusinessType(b)
{
    new string[30];
    switch(BusinessInfo[b][bType])
    {
    	case 7: string = "Restaurant";
    	case 6: string = "Bank";
    	case 5: string = "Hospital";
        case 4: string = "Police Station";
        case 3: string = "24/7";
        case 2: string = "Club";
        case 1: string = "Bar";
        case 0: string = "Clothes Shop";
    }
    return string;
}

IsPlayerNearBizEnt(playerid)
{
    for(new b = 1; b < sizeof(BusinessInfo); b++)
    {
        if(IsPlayerInRangeOfPoint(playerid, 4.0, BusinessInfo[b][bEntranceX], BusinessInfo[b][bEntranceY], BusinessInfo[b][bEntranceZ])) return b;
    }
    return -1;
}

IsPlayerNearHouseEnt(playerid)
{
    for(new h = 1; h < sizeof(HouseInfo); h++)
    {
        if(IsPlayerInRangeOfPoint(playerid, 4.0, HouseInfo[h][hEntranceX], HouseInfo[h][hEntranceY], HouseInfo[h][hEntranceZ])) return h;
    }
    return -1;
}

IsPlayerInsideHouse(playerid)
{
	new hworld = GetPlayerVirtualWorld(playerid);
 	if(!GetPlayerInterior(playerid)) return SCM(playerid, COLOR_LIGHTRED, "You are not inside any house.");
  	for(new h = 1; h < sizeof(HouseInfo); h++)
  	{
   		if(hworld == HouseInfo[h][hInsideWorld]) return h;
  	}
    return -1;
}

IsPlayerInsideBiz(playerid)
{
	new bworld = GetPlayerVirtualWorld(playerid);
    for(new b = 1; b < sizeof(BusinessInfo); b++)
    {
        if(bworld == PlayerInfo[playerid][HouseID]) return b;
    }
    return -1;
}

forward TimeCycle(playerid);
public TimeCycle(playerid)
{
	ServerTime++;
	SetWorldTime(ServerTime);

	new string[48];
    format(string, sizeof(string), "%d:00", ServerTime);
    TextDrawSetString(ServerTimeTXT,string);

	if(ServerTime == 7)//if servetime variable is at 23 it puts it the variable to 0
    {
        SetWeather(40);
    }
   	if(ServerTime == 8)//if servetime variable is at 23 it puts it the variable to 0
    {
        SetWeather(40);
    }
   	if(ServerTime == 13)//if servetime variable is at 23 it puts it the variable to 0
    {
        SetWeather(0);
    }
   	if(ServerTime == 18)//if servetime variable is at 23 it puts it the variable to 0
    {
        if(random(2) != 1) return 0;
        SetWeather(RandomSet(8,4,7));
    }
   	if(ServerTime == 19)//if servetime variable is at 23 it puts it the variable to 0
    {
        SetWeather(0);
    }
    if(ServerTime == 23)//if servetime variable is at 23 it puts it the variable to 0
    {
        ServerTime = 0;
        SetWeather(0);
    }
    if(ServerTime == 1)//if servetime variable is at 23 it puts it the variable to 0
    {
        SetWeather(17);
    }
    return 1;
}

Float: GetArmour(id)
{
    new Float: pp;
    GetPlayerArmour(id,pp);
    return pp;
}

forward DrugEnd(playerid);
public DrugEnd(playerid)
{
    SetPlayerDrunkLevel(playerid, 0);
    SetPlayerWeather(playerid, 0);
    
    IsSmokingJoint[playerid] = 0;
    IsSmokingCigarette[playerid] = 0;
    IsDrinkingBeer[playerid] = 0;
    SCM(playerid, -1, "* You're coming down from the trip.");
    return 1;
}

forward MarijuanaEffect(playerid);
public MarijuanaEffect(playerid)
{
	SetPlayerDrunkLevel (playerid, 5000);
 	SetPlayerWeather(playerid, 52);
 	
 	SetTimerEx("DrugEnd", 1200000, 0, "i", playerid);
 	SCM(playerid, COLOR_GOLD, "* Seems like that marijuana you smoked is starting to take effect.");
    return 1;
}

forward CocaineEffect(playerid);
public CocaineEffect(playerid)
{
	new
	Float: parmour;
	
	GetPlayerArmour(playerid, parmour);
	SetPlayerDrunkLevel (playerid, 1000);
	SetPlayerWeather(playerid, 51);
	GivePlayerArmour(playerid, 5);

 	SetTimerEx("DrugEnd", 300000, 0, "i", playerid);
 	SCM(playerid, COLOR_GOLD, "* Seems like that cocaine you snorted is starting to take effect.");
  	IsCocaineHigh[playerid] = 0;
    return 1;
}

forward LSDEffect(playerid);
public LSDEffect(playerid)
{
	new
	Float: parmour;

 	GetPlayerArmour(playerid, parmour);
	SetPlayerDrunkLevel(playerid, 500000);
	SetPlayerWeather(playerid, 700);
	GivePlayerArmour(playerid, 10);

 	SetTimerEx("DrugEnd", 300000, 0, "i", playerid);
 	SCM(playerid, COLOR_GOLD, "* Seems like that LSD you took is starting to take effect.");
  	IsLSDHigh[playerid] = 0;
    return 1;
}

forward LoadPlayerSpawnData(playerid);
public LoadPlayerSpawnData(playerid)
{

	TextDrawShowForPlayer(playerid, ServerTimeTXT);
	SetPlayerInterior(playerid, 0);
	SetPlayerVirtualWorld(playerid, 0);
    SetPlayerSkin(playerid, PlayerInfo[playerid][pSkin]);
    SetPlayerPos(playerid, 1743.0449,-1861.1635,13.5779);
    SetPlayerHealth(playerid, 100);
    SetPlayerInterior( playerid, PlayerInfo[playerid][pInterior] );
    SetPlayerVirtualWorld( playerid, PlayerInfo[playerid][pVirtualWorld] );

	GivePlayerWeapon(playerid, PlayerInfo[playerid][pWeapon1], PlayerInfo[playerid][pAmmo1]);
	GivePlayerWeapon(playerid, PlayerInfo[playerid][pWeapon2], PlayerInfo[playerid][pAmmo2]);
	GivePlayerWeapon(playerid, PlayerInfo[playerid][pWeapon3], PlayerInfo[playerid][pAmmo3]);
	GivePlayerWeapon(playerid, PlayerInfo[playerid][pWeapon4], PlayerInfo[playerid][pAmmo4]);
	GivePlayerWeapon(playerid, PlayerInfo[playerid][pWeapon5], PlayerInfo[playerid][pAmmo5]);
	GivePlayerWeapon(playerid, PlayerInfo[playerid][pWeapon6], PlayerInfo[playerid][pAmmo6]);
	GivePlayerWeapon(playerid, PlayerInfo[playerid][pWeapon7], PlayerInfo[playerid][pAmmo7]);
	GivePlayerWeapon(playerid, PlayerInfo[playerid][pWeapon8], PlayerInfo[playerid][pAmmo8]);
	GivePlayerWeapon(playerid, PlayerInfo[playerid][pWeapon9], PlayerInfo[playerid][pAmmo9]);
	GivePlayerWeapon(playerid, PlayerInfo[playerid][pWeapon10], PlayerInfo[playerid][pAmmo10]);
	GivePlayerWeapon(playerid, PlayerInfo[playerid][pWeapon11], PlayerInfo[playerid][pAmmo11]);
	GivePlayerWeapon(playerid, PlayerInfo[playerid][pWeapon12], PlayerInfo[playerid][pAmmo12]);
	GivePlayerWeapon(playerid, PlayerInfo[playerid][pWeapon13], PlayerInfo[playerid][pAmmo13]);
	GivePlayerWeapon(playerid, PlayerInfo[playerid][pWeapon14], PlayerInfo[playerid][pAmmo14]);
}

stock IsVehicleOccupied(vehicleid) // Returns 1 if there is anyone in the vehicle
{
    foreach(Player,i)
    {
        if(IsPlayerInAnyVehicle(i))
        {
            if(GetPlayerVehicleID(i)==vehicleid)
            {
                return 1;
            }
            else
            {
                return 0;
            }
        }
    }
    return 1;
}

public OnPlayerPickUpPickup(playerid, pickupid)
{
    if(pickupid == Pickup[0])
    {
        GameTextForPlayer(playerid, "/takedrivingtest", 5000, 5);
    }
    if(pickupid == Pickup[1])
    {
        GameTextForPlayer(playerid, "/advertise", 5000, 5);
    }
    if(pickupid == Pickup[3])
    {
        GameTextForPlayer(playerid, "/train", 5000, 5);
    }
    if(pickupid == Pickup[4])
    {
        GameTextForPlayer(playerid, "/train", 5000, 5);
    }
    if(pickupid == Pickup[5])
    {
        GameTextForPlayer(playerid, "/buy", 5000, 5);
    }
    if(pickupid == Pickup[6])
    {
        GameTextForPlayer(playerid, "/buy", 5000, 5);
    }
    if(pickupid == Pickup[7])
    {
        GameTextForPlayer(playerid, "/buy", 5000, 5);
    }
    if(pickupid == Pickup[8])
    {
        GameTextForPlayer(playerid, "/buy", 5000, 5);
    }
    if(pickupid == Pickup[9])
    {
        GameTextForPlayer(playerid, "/buyboombox", 5000, 5);
    }
    return 1;
}

forward LoadInterior(playerid);
public LoadInterior(playerid)
{
    TogglePlayerControllable(playerid,1);
    return 1;
}

forward AdvertiseAgain(playerid);
public AdvertiseAgain(playerid)
{
	AdvertiseAllowed[playerid] = 0;
	return 1;
}

forward ResetPlayerStats(playerid);
public ResetPlayerStats(playerid)
{
    ResetPlayerCash(playerid);
    PlayerInfo[playerid][pAdmin] = 0;
    PlayerInfo[playerid][pCigarettes] = 0;
    PlayerInfo[playerid][dMarijuana] = 0;
    PlayerInfo[playerid][dLSD] = 0;
    PlayerInfo[playerid][dCocaine] = 0;
    Dice[playerid] = 0;
    PlayerInfo[playerid][pRespect] = 0;
    PlayerInfo[playerid][pDeaths] = 0;
    PlayerInfo[playerid][pKills] = 0;
    PlayerInfo[playerid][pBankAccount] = 0;
    PlayerInfo[playerid][pAccountdata] = 0;
    PlayerInfo[playerid][pNumber] = 0;
    PlayerInfo[playerid][pSkin] = 0;
    PlayerInfo[playerid][pLevel] = 1;
    PlayerInfo[playerid][BusinessMoney] = 0;
    PlayerInfo[playerid][BizID] = 0;
    PlayerInfo[playerid][pDriverLicense] = 0;
    gPlayerLoggin{playerid} = 1;
	PlayerInfo[playerid][pAge] = 0;
	PlayerInfo[playerid][pGender] = 0;
	PlayerInfo[playerid][pInJail] = 0;
	PlayerInfo[playerid][pInJailTime] = 0;
	PlayerInfo[playerid][pFightingStyle] = 1;
	masknumber[playerid] = 1000 + random(9999);
 	PlayerInfo[playerid][pXPos] = 0;
 	PlayerInfo[playerid][pYPos] = 0;
 	PlayerInfo[playerid][pZPos] = 0;
 	PlayerInfo[playerid][pInterior] = 0;
 	PlayerInfo[playerid][pVirtualWorld] = 0;
 	isAlive[playerid] = true;
 	rentingVehicle[playerid] = false;
 	PlayerInfo[playerid][pExperience] = 0;
 	Player_Greet[playerid] = INVALID_PLAYER_ID;
 	
	RefuelTime[playerid] = 0;
	TrackCar[playerid] = 0;

	SpeedoText[playerid] = TextDrawCreate(180.000, 362.000," ");
	TextDrawAlignment(SpeedoText[playerid], 1);
	TextDrawFont(SpeedoText[playerid],2);
	TextDrawLetterSize(SpeedoText[playerid], 0.310, 1.400);
	TextDrawSetShadow(SpeedoText[playerid],0);
	TextDrawUseBox(SpeedoText[playerid], 1);
	TextDrawBoxColor(SpeedoText[playerid], 0x99);
	TextDrawTextSize(SpeedoText[playerid], 520.000, 0.000);

	PlayerInfo[playerid][pWeapon1] = 0;
	PlayerInfo[playerid][pAmmo1] = 0;
	PlayerInfo[playerid][pWeapon2] = 0;
	PlayerInfo[playerid][pAmmo2] = 0;
	PlayerInfo[playerid][pWeapon3] = 0;
	PlayerInfo[playerid][pAmmo3] = 0;
	PlayerInfo[playerid][pWeapon4] = 0;
	PlayerInfo[playerid][pAmmo4] = 0;
	PlayerInfo[playerid][pWeapon5] = 0;
	PlayerInfo[playerid][pAmmo5] = 0;
	PlayerInfo[playerid][pWeapon6] = 0;
	PlayerInfo[playerid][pAmmo6] = 0;
	PlayerInfo[playerid][pWeapon7] = 0;
	PlayerInfo[playerid][pAmmo7] = 0;
	PlayerInfo[playerid][pWeapon8] = 0;
	PlayerInfo[playerid][pAmmo8] = 0;
	PlayerInfo[playerid][pWeapon9] = 0;
	PlayerInfo[playerid][pAmmo9] = 0;
	PlayerInfo[playerid][pWeapon10] = 0;
	PlayerInfo[playerid][pAmmo10] = 0;
	PlayerInfo[playerid][pWeapon11] = 0;
	PlayerInfo[playerid][pAmmo11] = 0;
	PlayerInfo[playerid][pWeapon12] = 0;
	PlayerInfo[playerid][pAmmo12] = 0;
	PlayerInfo[playerid][pWeapon13] = 0;
	PlayerInfo[playerid][pAmmo13] = 0;
	PlayerInfo[playerid][pWeapon14] = 0;
	PlayerInfo[playerid][pAmmo14] = 0;
	
 	SetPlayerSkillLevel(playerid, WEAPONSKILL_PISTOL, 1);
 	SetPlayerSkillLevel(playerid, WEAPONSKILL_MICRO_UZI, 1);
 	SetPlayerSkillLevel(playerid, WEAPONSKILL_SPAS12_SHOTGUN, 1);
 	SetPlayerSkillLevel(playerid, WEAPONSKILL_SAWNOFF_SHOTGUN, 1);
}

forward ResetWeapons(playerid);
public ResetWeapons(playerid)
{
	PlayerInfo[playerid][pWeapon1] = 0;
	PlayerInfo[playerid][pAmmo1] = 0;
	PlayerInfo[playerid][pWeapon2] = 0;
	PlayerInfo[playerid][pAmmo2] = 0;
	PlayerInfo[playerid][pWeapon3] = 0;
	PlayerInfo[playerid][pAmmo3] = 0;
	PlayerInfo[playerid][pWeapon4] = 0;
	PlayerInfo[playerid][pAmmo4] = 0;
	PlayerInfo[playerid][pWeapon5] = 0;
	PlayerInfo[playerid][pAmmo5] = 0;
	PlayerInfo[playerid][pWeapon6] = 0;
	PlayerInfo[playerid][pAmmo6] = 0;
	PlayerInfo[playerid][pWeapon7] = 0;
	PlayerInfo[playerid][pAmmo7] = 0;
	PlayerInfo[playerid][pWeapon8] = 0;
	PlayerInfo[playerid][pAmmo8] = 0;
	PlayerInfo[playerid][pWeapon9] = 0;
	PlayerInfo[playerid][pAmmo9] = 0;
	PlayerInfo[playerid][pWeapon10] = 0;
	PlayerInfo[playerid][pAmmo10] = 0;
	PlayerInfo[playerid][pWeapon11] = 0;
	PlayerInfo[playerid][pAmmo11] = 0;
	PlayerInfo[playerid][pWeapon12] = 0;
	PlayerInfo[playerid][pAmmo12] = 0;
	PlayerInfo[playerid][pWeapon13] = 0;
	PlayerInfo[playerid][pAmmo13] = 0;
	PlayerInfo[playerid][pWeapon14] = 0;
	PlayerInfo[playerid][pAmmo14] = 0;
}

forward LoadFightingStyle(playerid);
public LoadFightingStyle(playerid)
{
	if(PlayerInfo[playerid][pFightingStyle] == 1)
	{
	    SetPlayerFightingStyle (playerid, FIGHT_STYLE_NORMAL);
	}
	else if(PlayerInfo[playerid][pFightingStyle] == 2)
	{
	    SetPlayerFightingStyle (playerid, FIGHT_STYLE_BOXING);
	}
	else if(PlayerInfo[playerid][pFightingStyle] == 3)
	{
	    SetPlayerFightingStyle (playerid, FIGHT_STYLE_KNEEHEAD);
	}
	else if(PlayerInfo[playerid][pFightingStyle] == 4)
	{
	    SetPlayerFightingStyle (playerid, FIGHT_STYLE_KUNGFU);
	}
}

public OnPlayerTakeDamage(playerid, issuerid, Float:amount, weaponid)
{
    new
	Float:Pos[3], string[24];
    GetPlayerPos(playerid, Pos[0], Pos[1], Pos[2]);

	SetTimerEx("Delay", 1000, false, "i", playerid);
	switch(hit[playerid])
	{
	    case 0:
	    {
	    	format(string, 4, "%.1f", amount);
			DamageLabel[0] = Create3DTextLabel(string, 0xFF0000FF, Pos[0], Pos[1], Pos[2] + 1.0, 20.0, 0, 0);
			hit[playerid] = -1;
	    }
	    case 1:
	    {
	        Delete3DTextLabel(Text3D:DamageLabel[0]);
	    	format(string, 4, "%.1f", amount);
			DamageLabel[1] = Create3DTextLabel(string, 0xFF0000FF, Pos[0], Pos[1], Pos[2] + 1.0, 20.0, 0, 0);
			hit[playerid] = -1;
	    }
  	  	case 2:
	    {
    		Delete3DTextLabel(Text3D:DamageLabel[1]);
	    	format(string, 4, "%.1f", amount);
			DamageLabel[2] = Create3DTextLabel(string, 0xFF0000FF, Pos[0], Pos[1], Pos[2] + 1.0, 20.0, 0, 0);
	    }
	    case 3:
	    {
    		Delete3DTextLabel(Text3D:DamageLabel[2]);
	    	format(string, 4, "%.1f", amount);
			DamageLabel[3] = Create3DTextLabel(string, 0xFF0000FF, Pos[0], Pos[1], Pos[2] + 1.0, 20.0, 0, 0);
	    }
	    case 4:
	    {
    		Delete3DTextLabel(Text3D:DamageLabel[3]);
	    	format(string, 4, "%.1f", amount);
			DamageLabel[4] = Create3DTextLabel(string, 0xFF0000FF, Pos[0], Pos[1], Pos[2] + 1.0, 20.0, 0, 0);
	    }
	    case 5:
	    {
    		Delete3DTextLabel(Text3D:DamageLabel[4]);
	    	format(string, 4, "%.1f", amount);
			DamageLabel[5] = Create3DTextLabel(string, 0xFF0000FF, Pos[0], Pos[1], Pos[2] + 1.0, 20.0, 0, 0);
	    }
	    case 6:
	    {
    		Delete3DTextLabel(Text3D:DamageLabel[4]);
	    	format(string, 4, "%.1f", amount);
			DamageLabel[6] = Create3DTextLabel(string, 0xFF0000FF, Pos[0], Pos[1], Pos[2] + 1.0, 20.0, 0, 0);
	    }
	    case 7:
	    {
    		Delete3DTextLabel(Text3D:DamageLabel[4]);
	    	format(string, 4, "%.1f", amount);
			DamageLabel[7] = Create3DTextLabel(string, 0xFF0000FF, Pos[0], Pos[1], Pos[2] + 1.0, 20.0, 0, 0);
	    }
	}
    return 1;
}

forward Delay(playerid);
public Delay(playerid)
{
	Delete3DTextLabel(Text3D:DamageLabel[0]);
	Delete3DTextLabel(Text3D:DamageLabel[1]);
	Delete3DTextLabel(Text3D:DamageLabel[2]);
	Delete3DTextLabel(Text3D:DamageLabel[3]);
	Delete3DTextLabel(Text3D:DamageLabel[4]);
	Delete3DTextLabel(Text3D:DamageLabel[5]);
	Delete3DTextLabel(Text3D:DamageLabel[6]);
	Delete3DTextLabel(Text3D:DamageLabel[7]);
}

forward StartIntro(playerid); // From water scene
public StartIntro(playerid)
{
    SetTimerEx("Camera1", 20000, false, "i", playerid);
    TogglePlayerSpectating(playerid, 1);
	FadeColorForPlayer(playerid,0,0,0,255,0,0,0,0,15,0);
    InterpolateCameraPos(playerid, 724.8024,-2001.6941,-12.0839, 722.7170,-1603.7065,64.4452, 25000, CAMERA_MOVE);
    InterpolateCameraLookAt(playerid, 722.7170,-1603.7065,64.4452, 724.8024,-2001.6941,-12.0839, 25000, CAMERA_MOVE);
   	PlayAudioStreamForPlayer(playerid, "http://k007.kiwi6.com/hotlink/zphpaqno50/losangeles.mp3");
	for(new i = 0; i < 50; i++) SCM(playerid, COLOR_WHITE," ");
   	TextDrawShowForPlayer(playerid,Textdraw0);
   	TextDrawShowForPlayer(playerid,Textdraw1);
   	TextDrawShowForPlayer(playerid,Textdraw2);
   	TextDrawShowForPlayer(playerid,Textdraw3);
   	TextDrawShowForPlayer(playerid,Textdraw4);
    return 1;
}

forward Camera1(playerid); // Bank Scene
public Camera1(playerid)
{
    SetTimerEx("Camera2", 15000, false, "i", playerid);
    InterpolateCameraPos(playerid, 1716.1949,-1303.5061,13.3906, 1728.7573,-1282.2025,13.5534, 15000, CAMERA_MOVE);
    InterpolateCameraLookAt(playerid, 1728.7573,-1282.2025,13.5534, 1728.7573,-1282.2025,13.5534, 15000, CAMERA_MOVE);
   	TextDrawHideForPlayer(playerid,Textdraw2);
   	TextDrawHideForPlayer(playerid,Textdraw3);
   	TextDrawHideForPlayer(playerid,Textdraw4);
   	TextDrawShowForPlayer(playerid,Textdraw9);
   	TextDrawShowForPlayer(playerid,Textdraw10);
   	TextDrawShowForPlayer(playerid,Textdraw11);
    return 1;
}

forward Camera2(playerid); // Downtown Restaurant Scene
public Camera2(playerid)
{
	SetTimerEx("Camera3", 15000, false, "i", playerid);
    InterpolateCameraPos(playerid, 1631.8916,-1204.1125,19.7890, 1544.4659,-1204.0747,20.0736, 15000, CAMERA_MOVE);
    InterpolateCameraLookAt(playerid, 1631.8916,-1204.1125,19.7890, 1544.4659,-1204.0747,20.0736, 15000, CAMERA_MOVE);
   	TextDrawHideForPlayer(playerid,Textdraw9);
   	TextDrawHideForPlayer(playerid,Textdraw10);
   	TextDrawHideForPlayer(playerid,Textdraw11);
   	TextDrawShowForPlayer(playerid,Textdraw5);
   	TextDrawShowForPlayer(playerid,Textdraw12);
   	TextDrawShowForPlayer(playerid,Textdraw13);
	return 1;
}

forward Camera3(playerid); // Jefferson Alley Scene
public Camera3(playerid)
{
	SetTimerEx("Camera4", 15000, false, "i", playerid);
 	InterpolateCameraPos(playerid,2158.0725,-1260.8678,23.9902, 2085.0762,-1261.1925,23.9924, 15000, CAMERA_MOVE);
 	InterpolateCameraLookAt(playerid, 2085.0762,-1261.1925,23.9924, 2158.0725,-1260.8678,23.9902, 15000, CAMERA_MOVE);
   	TextDrawHideForPlayer(playerid,Textdraw5);
   	TextDrawHideForPlayer(playerid,Textdraw12);
   	TextDrawHideForPlayer(playerid,Textdraw13);
   	TextDrawShowForPlayer(playerid,Textdraw6);
   	TextDrawShowForPlayer(playerid,Textdraw14);
   	TextDrawShowForPlayer(playerid,Textdraw15);
	return 1;
}

forward Camera4(playerid); // LAPD Scene
public Camera4(playerid)
{
 	InterpolateCameraPos(playerid,1514.9663,-1676.1392,14.0469, 1524.1227,-1675.9989,13.5469, 15000, CAMERA_MOVE);
 	InterpolateCameraLookAt(playerid,1514.9663,-1676.1392,14.0469, 1524.1227,-1675.9989,13.5469, 15000, CAMERA_MOVE);
	SetTimerEx("Camera5", 15000, false, "i", playerid);
   	TextDrawHideForPlayer(playerid,Textdraw6);
   	TextDrawHideForPlayer(playerid,Textdraw14);
   	TextDrawHideForPlayer(playerid,Textdraw15);
   	TextDrawShowForPlayer(playerid,Textdraw7);
   	TextDrawShowForPlayer(playerid,Textdraw16);
	return 1;
}

forward Camera5(playerid); // City Hall Scene
public Camera5(playerid)
{
	SetTimerEx("AgeSetup", 15000, false, "i", playerid);
	InterpolateCameraPos(playerid,1471.3602,-1682.5798,14.0469, 1473.1530,-1697.3690,14.0469, 15000, CAMERA_MOVE);
	InterpolateCameraLookAt(playerid,1473.0674,-1688.8176,14.0469, 1480.6729,-1771.5760,18.7958, 15000, CAMERA_MOVE);
	TextDrawHideForPlayer(playerid,Textdraw7);
   	TextDrawHideForPlayer(playerid,Textdraw16);
	TextDrawShowForPlayer(playerid,Textdraw8);
	TextDrawShowForPlayer(playerid,Textdraw17);
	TextDrawShowForPlayer(playerid,Textdraw18);
	return 1;
}

forward AgeSetup(playerid); // Tutorial Done
public AgeSetup(playerid)
{
	SpawnPlayer(playerid);
	TogglePlayerControllable(playerid, 0);
	SetPlayerPos(playerid, 280.1480,1354.4714,343.1370);
	SetPlayerFacingAngle(playerid, 359.6018);
	SetPlayerCameraPos(playerid, 279.9863,1357.4241,343.1370);
	SetPlayerCameraLookAt(playerid, 280.1480,1354.4714,343.1370);
	SetPlayerInterior(playerid, 0);
	TextDrawHideForPlayer(playerid,Textdraw8);
	TextDrawHideForPlayer(playerid,Textdraw17);
	TextDrawHideForPlayer(playerid,Textdraw18);
	ShowPlayerDialog(playerid, DIALOG_AGE, DIALOG_STYLE_INPUT, "Age?", "Please type in your characters age below. (7-100)", "Submit", "Cancel");
	return 1;
}

forward TutorialDone(playerid); // Tutorial Done
public TutorialDone(playerid)
{
    SpawnPlayer(playerid);
    TogglePlayerSpectating(playerid, 0);
    SetPlayerSkin(playerid, PlayerInfo[playerid][pSkin]);
   	TogglePlayerControllable(playerid, 1);
	FadeColorForPlayer(playerid,0,0,0,0,0,0,0,255,15,0);
	SCM(playerid, COLOR_GOLD, "* Thank you for choosing Illusional Roleplay, we hope you enjoy your stay.");
	TextDrawHideForPlayer(playerid,Textdraw0);
	TextDrawHideForPlayer(playerid,Textdraw1);
	return 1;
}

forward LoadDeathAnim(playerid);
public LoadDeathAnim(playerid)
{
	ApplyAnimation(playerid,"CRACK","crckdeth2",4.1,1,1,1,1,1,1);
	return 1;
}


forward OperationDone(playerid);
public OperationDone(playerid)
{
	FadeColorForPlayer(playerid,0,0,0,255,0,0,0,0,15,0);
	SCM(playerid, COLOR_GOLD, "* You have been treated at the hospital. The hospital bill is $50.");
	SetPlayerPos(playerid, 1173.2512,-1325.4686,15.3943);
	GivePlayerCash(playerid, -50);
	SetPlayerHealth(playerid, 90.0);
	TogglePlayerControllable(playerid, 1);
 	SetPlayerInterior(playerid, 0);
	return 1;
}

forward DiveAnim(playerid);
public DiveAnim(playerid)
{
	new Float:X, Float:Y, Float:Z;
	GetPlayerPos(playerid, X, Y, Z);
	ClearAnimations(playerid);
	SetPlayerPos(playerid, X, Y -9, Z);
	return 1;
}

stock UpdateWorldWeather()
{
	new next_weather_prob = random(100);
	if(next_weather_prob < 70) 		SetWeather(fine_weather_ids[random(sizeof(fine_weather_ids))]);
	else if(next_weather_prob < 95) SetWeather(foggy_weather_ids[random(sizeof(foggy_weather_ids))]);
	else							SetWeather(wet_weather_ids[random(sizeof(wet_weather_ids))]);
}

forward UpdateTimeAndWeather();
public UpdateTimeAndWeather()
{
	// Update time
    gettime(hour, minute);

   	format(timestr,32,"%02d:%02d",hour,minute);
   	TextDrawSetString(txtTimeDisp,timestr);
   	SetWorldTime(hour);

	new x=0;
	while(x!=MAX_PLAYERS)
	{
 		if(IsPlayerConnected(x) && GetPlayerState(x) != PLAYER_STATE_NONE)
 		{
 			SetPlayerTime(x,hour,minute);
		}
		x++;
	}

	/* Update weather every hour
	if(last_weather_update == 0) {
	    UpdateWorldWeather(); }
	last_weather_update++;
	if(last_weather_update == 60) {
	    last_weather_update = 0; }*/
}

RemoveWeapons(playerid)
{
	PlayerInfo[playerid][pWeapon1] = 0;
	PlayerInfo[playerid][pWeapon2] = 0;
	PlayerInfo[playerid][pWeapon3] = 0;
	PlayerInfo[playerid][pWeapon4] = 0;
	PlayerInfo[playerid][pWeapon5] = 0;
	PlayerInfo[playerid][pWeapon6] = 0;
	PlayerInfo[playerid][pWeapon7] = 0;
	PlayerInfo[playerid][pWeapon8] = 0;
	PlayerInfo[playerid][pWeapon9] = 0;
	PlayerInfo[playerid][pWeapon10] = 0;
	PlayerInfo[playerid][pWeapon11] = 0;
	PlayerInfo[playerid][pWeapon12] = 0;
	PlayerInfo[playerid][pWeapon13] = 0;
	PlayerInfo[playerid][pWeapon14] = 0;
	PlayerInfo[playerid][pAmmo1] = 0;
	PlayerInfo[playerid][pAmmo2] = 0;
	PlayerInfo[playerid][pAmmo3] = 0;
	PlayerInfo[playerid][pAmmo4] = 0;
	PlayerInfo[playerid][pAmmo5] = 0;
	PlayerInfo[playerid][pAmmo6] = 0;
	PlayerInfo[playerid][pAmmo7] = 0;
	PlayerInfo[playerid][pAmmo8] = 0;
	PlayerInfo[playerid][pAmmo9] = 0;
	PlayerInfo[playerid][pAmmo10] = 0;
	PlayerInfo[playerid][pAmmo11] = 0;
	PlayerInfo[playerid][pAmmo12] = 0;
	PlayerInfo[playerid][pAmmo13] = 0;
	PlayerInfo[playerid][pAmmo14] = 0;
	ResetPlayerWeapons(playerid);
}

RemoveDrugs(playerid)
{
	PlayerInfo[playerid][dLSD] = 0;
	PlayerInfo[playerid][dMarijuana] = 0;
	PlayerInfo[playerid][dCocaine] = 0;
}

stock IsRPName(const name[], max_underscores = 2)
{
    new underscores = 0;
    if (name[0] < 'A' || name[0] > 'Z') return false; // First letter is not capital
    for(new i = 1; i < strlen(name); i++)
    {
        if(name[i] != '_' && (name[i] < 'A' || name[i] > 'Z') && (name[i] < 'a' || name[i] > 'z')) return false; // a-zA-Z_
        if( (name[i] >= 'A' && name[i] <= 'Z') && (name[i - 1] != '_') ) return false; // unneeded capital letter
        if(name[i] == '_')
        {
            underscores++;
            if(underscores > max_underscores || i == strlen(name)) return false; // More underlines than limit, or underline at the last pos
            if(name[i + 1] < 'A' || name[i + 1] > 'Z') return false; // Not a capital letter after underline
        }
    }
    if (underscores == 0) return false; // No underline detected
    return true;
}

OnePlayAnim(playerid,animlib[],animname[], Float:Speed, looping, lockx, locky, lockz, lp, forcesync)
{
	ApplyAnimation(playerid, animlib, animname, Speed, looping, lockx, locky, lockz, lp, forcesync);
}


LoopingAnim(playerid,animlib[],animname[], Float:Speed, looping, lockx, locky, lockz, lp, forcesync)
{
    gPlayerUsingLoopingAnim[playerid] = 1;
    ApplyAnimation(playerid, animlib, animname, Speed, looping, lockx, locky, lockz, lp, forcesync);
}

BackAnim(playerid,animlib[],animname[], Float:Speed, looping, lockx, locky, lockz, lp,animback, forcesync)
{
    BackOut[playerid] = animback;
    ApplyAnimation(playerid, animlib, animname, Speed, looping, lockx, locky, lockz, lp, forcesync);
    animation[playerid]++;
}

stock PlayerName(playerid)
{
	new pName[MAX_PLAYER_NAME];
	GetPlayerName(playerid, pName, MAX_PLAYER_NAME);
	return pName;
}

stock IsPlayerSpawned(playerid)
{
	switch(GetPlayerState(playerid))
	{
		case 1,2,3: return 1;
	}
	return 0;
}

stock IsMeleeWeapon(weaponid)
{
	switch(weaponid)
	{
		case 2 .. 15, 40, 44 .. 46: return 1;
	}
	return 0;
}

stock RemovePlayerWeapon(playerid, weaponid)
{
	new WeaponData[12][2];
	for(new i=1; i < sizeof(WeaponData); i++)
	{
		GetPlayerWeaponData(playerid, i, WeaponData[i][0], WeaponData[i][1]);
	}
	ResetPlayerWeapons(playerid);
	for(new i=1; i < sizeof(WeaponData); i++)
	{
		if(WeaponData[i][0] != weaponid)
		{
			GivePlayerWeapon(playerid, WeaponData[i][0], WeaponData[i][1]);
		}
	}
}

stock IsBicycle(vehicleid)
{
	switch(GetVehicleModel(vehicleid))
	{
		case 481,509,510: return 1;
	}
	return 0;
}

stock PlayerToPlayer(playerid, targetid, Float:dist)
{
	new Float:pos[3];
	GetPlayerPos(targetid, pos[0], pos[1], pos[2]);
	return IsPlayerInRangeOfPoint(playerid, dist, pos[0], pos[1], pos[2]);
}

stock PlayerToVehicle(playerid, vehicleid, Float:dist)
{
	new Float:pos[3];
	GetVehiclePos(vehicleid, pos[0], pos[1], pos[2]);
	return IsPlayerInRangeOfPoint(playerid, dist, pos[0], pos[1], pos[2]);
}

stock GetClosestVehicle(playerid)
{
	new Float:x, Float:y, Float:z;
	new Float:dist, Float:closedist=9999, closeveh;
	for(new i=1; i < MAX_VEHICLES; i++)
	{
		if(GetVehiclePos(i, x, y, z))
		{
			dist = GetPlayerDistanceFromPoint(playerid, x, y, z);
			if(dist < closedist)
			{
				closedist = dist;
				closeveh = i;
			}
		}
	}
	return closeveh;
}

stock ToggleEngine(vehicleid, toggle)
{
	GetVehicleParamsEx(vehicleid, engine, lights, alarm, doors, bonnet, boot, objective);
	SetVehicleParamsEx(vehicleid, toggle, lights, alarm, doors, bonnet, boot, objective);
}

stock ToggleAlarm(vehicleid, toggle)
{
	GetVehicleParamsEx(vehicleid, engine, lights, alarm, doors, bonnet, boot, objective);
	SetVehicleParamsEx(vehicleid, engine, lights, toggle, doors, bonnet, boot, objective);
}

stock ToggleDoors(vehicleid, toggle)
{
	GetVehicleParamsEx(vehicleid, engine, lights, alarm, doors, bonnet, boot, objective);
	SetVehicleParamsEx(vehicleid, engine, lights, alarm, toggle, bonnet, boot, objective);
}

stock ToggleBoot(vehicleid, toggle)
{
	GetVehicleParamsEx(vehicleid, engine, lights, alarm, doors, bonnet, boot, objective);
	SetVehicleParamsEx(vehicleid, engine, lights, alarm, doors, bonnet, toggle, objective);
}

stock IsNumeric(const string[])
{
	for(new i=0; string[i]; i++)
	{
		if(string[i] < '0' || string[i] > '9') return 0;
	}
	return 1;
}

stock GetVehicleModelIDFromName(const vname[])
{
	for(new i=0; i < sizeof(VehicleNames); i++)
	{
		if(strfind(VehicleNames[i], vname, true) != -1) return i + 400;
	}
	return -1;
}

stock GetPlayer2DZone(playerid)
{
	new zone[32] = "San Andreas";
	new Float:x, Float:y, Float:z;
	GetPlayerPos(playerid, x, y, z);
 	for(new i = 0; i < sizeof(SanAndreasZones); i++)
	{
		if(x >= SanAndreasZones[i][Zone_Area][0] && x <= SanAndreasZones[i][Zone_Area][3]
		&& y >= SanAndreasZones[i][Zone_Area][1] && y <= SanAndreasZones[i][Zone_Area][4])
		{
			strmid(zone, SanAndreasZones[i][Zone_Name], 0, 28);
			return zone;
		}
	}
	return zone;
}

stock GetPlayer3DZone(playerid)
{
	new zone[32] = "San Andreas";
	new Float:x, Float:y, Float:z;
	GetPlayerPos(playerid, x, y, z);
 	for(new i = 0; i < sizeof(SanAndreasZones); i++)
	{
		if(x >= SanAndreasZones[i][Zone_Area][0] && x <= SanAndreasZones[i][Zone_Area][3]
		&& y >= SanAndreasZones[i][Zone_Area][1] && y <= SanAndreasZones[i][Zone_Area][4]
		&& z >= SanAndreasZones[i][Zone_Area][2] && z <= SanAndreasZones[i][Zone_Area][5])
		{
			strmid(zone, SanAndreasZones[i][Zone_Name], 0, 28);
			return zone;
		}
	}
	return zone;
}

stock GetPlayerSpeed(playerid, bool:kmh = true)
{
	new
		Float:xx,
		Float:yy,
		Float:zz,
		Float:pSpeed;

	if(IsPlayerInAnyVehicle(playerid))
	{
		GetVehicleVelocity(GetPlayerVehicleID(playerid),xx,yy,zz);
	}
	else
	{
		GetPlayerVelocity(playerid,xx,yy,zz);
	}

	pSpeed = floatsqroot((xx * xx) + (yy * yy) + (zz * zz));
	return kmh ? floatround((pSpeed * 165.12)) : floatround((pSpeed * 103.9));
}

IsAdmin(playerid, level)
{
	if(IsPlayerAdmin(playerid)) return 1;
	if(CallRemoteFunction("GetPlayerAVSAdmin", "d", playerid) >= level) return 1;
	return 0;
}

LoadVehicles()
{
	new string[64];
	new File:handle, count;
	new filename[64], line[256], s, key[64];
	for(new i=1; i < MAX_DVEHICLES; i++)
	{
		format(filename, sizeof(filename), VEHICLE_FILE_PATH "v%d.ini", i);
		if(!fexist(filename)) continue;
		handle = fopen(filename, io_read);
		while(fread(handle, line))
		{
			StripNL(line);
			s = strfind(line, "=");
			if(!line[0] || s < 1) continue;
			strmid(key, line, 0, s++);
			if(strcmp(key, "Created") == 0) VehicleCreated[i] = strval(line[s]);
			else if(strcmp(key, "Model") == 0) VehicleModel[i] = strval(line[s]);
			else if(strcmp(key, "Pos") == 0) sscanf(line[s], "p<,>ffff", VehiclePos[i][0], VehiclePos[i][1],
				VehiclePos[i][2], VehiclePos[i][3]);
			else if(strcmp(key, "Colors") == 0) sscanf(line[s], "p<,>dd", VehicleColor[i][0], VehicleColor[i][1]);
			else if(strcmp(key, "Interior") == 0) VehicleInterior[i] = strval(line[s]);
			else if(strcmp(key, "VirtualWorld") == 0) VehicleWorld[i] = strval(line[s]);
			else if(strcmp(key, "Owner") == 0) strmid(VehicleOwner[i], line, s, sizeof(line));
			else if(strcmp(key, "NumberPlate") == 0) strmid(VehicleNumberPlate[i], line, s, sizeof(line));
			else if(strcmp(key, "Value") == 0) VehicleValue[i] = strval(line[s]);
			else if(strcmp(key, "Lock") == 0) VehicleLock[i] = strval(line[s]);
			else if(strcmp(key, "Alarm") == 0) VehicleAlarm[i] = strval(line[s]);
			else if(strcmp(key, "Paintjob") == 0) VehiclePaintjob[i] = strval(line[s]);
			else
			{
				for(new t=0; t < sizeof(VehicleTrunk[]); t++)
				{
					format(string, sizeof(string), "Trunk%d", t+1);
					if(strcmp(key, string) == 0) sscanf(line[s], "p<,>dd", VehicleTrunk[i][t][0], VehicleTrunk[i][t][1]);
				}
				for(new m=0; m < sizeof(VehicleMods[]); m++)
				{
					format(string, sizeof(string), "Mod%d", m);
					if(strcmp(key, string) == 0) VehicleMods[i][m] = strval(line[s]);
				}
			}
		}
		fclose(handle);
		if(VehicleCreated[i]) count++;
	}
	printf("  Loaded %d vehicles", count);
}

SaveVehicle(vehicleid)
{
	new filename[64], line[256];
	format(filename, sizeof(filename), VEHICLE_FILE_PATH "v%d.ini", vehicleid);
	new File:handle = fopen(filename, io_write);
	format(line, sizeof(line), "Created=%d\r\n", VehicleCreated[vehicleid]); fwrite(handle, line);
	format(line, sizeof(line), "Model=%d\r\n", VehicleModel[vehicleid]); fwrite(handle, line);
	format(line, sizeof(line), "Pos=%.3f,%.3f,%.3f,%.3f\r\n", VehiclePos[vehicleid][0], VehiclePos[vehicleid][1],
		VehiclePos[vehicleid][2], VehiclePos[vehicleid][3]);
	fwrite(handle, line);
	format(line, sizeof(line), "Colors=%d,%d\r\n", VehicleColor[vehicleid][0], VehicleColor[vehicleid][1]); fwrite(handle, line);
	format(line, sizeof(line), "Interior=%d\r\n", VehicleInterior[vehicleid]); fwrite(handle, line);
	format(line, sizeof(line), "VirtualWorld=%d\r\n", VehicleWorld[vehicleid]); fwrite(handle, line);
	format(line, sizeof(line), "Owner=%s\r\n", VehicleOwner[vehicleid]); fwrite(handle, line);
	format(line, sizeof(line), "NumberPlate=%s\r\n", VehicleNumberPlate[vehicleid]); fwrite(handle, line);
	format(line, sizeof(line), "Value=%d\r\n", VehicleValue[vehicleid]); fwrite(handle, line);
	format(line, sizeof(line), "Lock=%d\r\n", VehicleLock[vehicleid]); fwrite(handle, line);
	format(line, sizeof(line), "Alarm=%d\r\n", VehicleAlarm[vehicleid]); fwrite(handle, line);
	format(line, sizeof(line), "Paintjob=%d\r\n", VehiclePaintjob[vehicleid]); fwrite(handle, line);
	for(new t=0; t < sizeof(VehicleTrunk[]); t++)
	{
		format(line, sizeof(line), "Trunk%d=%d,%d\r\n", t+1, VehicleTrunk[vehicleid][t][0], VehicleTrunk[vehicleid][t][1]);
		fwrite(handle, line);
	}
	for(new m=0; m < sizeof(VehicleMods[]); m++)
	{
		format(line, sizeof(line), "Mod%d=%d\r\n", m, VehicleMods[vehicleid][m]);
		fwrite(handle, line);
	}
	fclose(handle);
}

UpdateVehicle(vehicleid, removeold)
{
	if(VehicleCreated[vehicleid])
	{
		if(removeold)
		{
			new Float:health;
			GetVehicleHealth(VehicleID[vehicleid], health);
			GetVehicleParamsEx(VehicleID[vehicleid], engine, lights, alarm, doors, bonnet, boot, objective);
			//new panels, doorsd, lightsd, tires;
			//GetVehicleDamageStatus(VehicleID[vehicleid], panels, doorsd, lightsd, tires);
			DestroyVehicle(VehicleID[vehicleid]);
			VehicleID[vehicleid] = CreateVehicle(VehicleModel[vehicleid], VehiclePos[vehicleid][0], VehiclePos[vehicleid][1],
				VehiclePos[vehicleid][2], VehiclePos[vehicleid][3], VehicleColor[vehicleid][0], VehicleColor[vehicleid][1], 3600);
			SetVehicleHealth(VehicleID[vehicleid], health);
			SetVehicleParamsEx(VehicleID[vehicleid], engine, lights, alarm, doors, bonnet, boot, objective);
			//UpdateVehicleDamageStatus(VehicleID[vehicleid], panels, doorsd, lightsd, tires);
		}
		else
		{
			VehicleID[vehicleid] = CreateVehicle(VehicleModel[vehicleid], VehiclePos[vehicleid][0], VehiclePos[vehicleid][1],
				VehiclePos[vehicleid][2], VehiclePos[vehicleid][3], VehicleColor[vehicleid][0], VehicleColor[vehicleid][1], 3600);
		}
		LinkVehicleToInterior(VehicleID[vehicleid], VehicleInterior[vehicleid]);
		SetVehicleVirtualWorld(VehicleID[vehicleid], VehicleWorld[vehicleid]);
		SetVehicleNumberPlate(VehicleID[vehicleid], VehicleNumberPlate[vehicleid]);
		for(new i=0; i < sizeof(VehicleMods[]); i++)
		{
			AddVehicleComponent(VehicleID[vehicleid], VehicleMods[vehicleid][i]);
		}
		ChangeVehiclePaintjob(VehicleID[vehicleid], VehiclePaintjob[vehicleid]);
		if(VehicleLock[vehicleid]) ToggleDoors(VehicleID[vehicleid], VEHICLE_PARAMS_ON);
		if(VehicleAlarm[vehicleid]) VehicleSecurity[VehicleID[vehicleid]] = 1;
		UpdateVehicleLabel(vehicleid, removeold);
	}
}

UpdateVehicleLabel(vehicleid, removeold)
{
	if(VehicleCreated[vehicleid] == VEHICLE_DEALERSHIP)
	{
		if(removeold)
		{
			Delete3DTextLabel(VehicleLabel[vehicleid]);
		}
		new labeltext[128];
		format(labeltext, sizeof(labeltext), ""COL_WHITE"%s\n"COL_BROWN"Price: "COL_WHITE"$%d", VehicleNames[VehicleModel[vehicleid]-400], VehicleValue[vehicleid]);
		VehicleLabel[vehicleid] = Create3DTextLabel(labeltext, 0xBB7700DD, 0, 0, 0, 10.0, 0);
		Attach3DTextLabelToVehicle(VehicleLabel[vehicleid], VehicleID[vehicleid], 0, 0, 0);
	}
}


IsValidVehicle(vehicleid)
{
	if(vehicleid < 1 || vehicleid >= MAX_DVEHICLES) return 0;
	if(VehicleCreated[vehicleid]) return 1;
	return 0;
}

GetFreeVehicleID()
{
	for(new i=1; i < MAX_DVEHICLES; i++)
	{
		if(!VehicleCreated[i]) return i;
	}
	return 0;
}

GetVehicleID(vehicleid)
{
	for(new i=1; i < MAX_DVEHICLES; i++)
	{
		if(VehicleCreated[i] && VehicleID[i] == vehicleid) return i;
	}
	return 0;
}

GetPlayerVehicles(playerid)
{
	new playername[24];
	GetPlayerName(playerid, playername, sizeof(playername));
	new count;
	for(new i=1; i < MAX_DVEHICLES; i++)
	{
		if(VehicleCreated[i] == VEHICLE_PLAYER && strcmp(VehicleOwner[i], playername) == 0)
		{
			count++;
		}
	}
	return count;
}

GetPlayerVehicleAccess(playerid, vehicleid)
{
	if(IsValidVehicle(vehicleid))
	{
		if(VehicleCreated[vehicleid] == VEHICLE_DEALERSHIP)
		{
			if(IsAdmin(playerid, 1))
			{
				return 1;
			}
		}
		else if(VehicleCreated[vehicleid] == VEHICLE_PLAYER)
		{
			if(strcmp(VehicleOwner[vehicleid], PlayerName(playerid)) == 0)
			{
				return 2;
			}
			else if(GetPVarInt(playerid, "CarKeys") == vehicleid)
			{
				return 1;
			}
		}
	}
	else
	{
		return 1;
	}
	return 0;
}

LoadDealerships()
{
	new File:handle, count;
	new filename[64], line[256], s, key[64];
	for(new i=1; i < MAX_DEALERSHIPS; i++)
	{
		format(filename, sizeof(filename), DEALERSHIP_FILE_PATH "d%d.ini", i);
		if(!fexist(filename)) continue;
		handle = fopen(filename, io_read);
		while(fread(handle, line))
		{
			StripNL(line);
			s = strfind(line, "=");
			if(!line[0] || s < 1) continue;
			strmid(key, line, 0, s++);
			if(strcmp(key, "Created") == 0) DealershipCreated[i] = strval(line[s]);
			else if(strcmp(key, "Pos") == 0) sscanf(line[s], "p<,>fff", DealershipPos[i][0],
				DealershipPos[i][1], DealershipPos[i][2]);
		}
		fclose(handle);
		if(DealershipCreated[i]) count++;
	}
	printf("  Loaded %d dealerships", count);
}

SaveDealership(dealerid)
{
	new filename[64], line[256];
	format(filename, sizeof(filename), DEALERSHIP_FILE_PATH "d%d.ini", dealerid);
	new File:handle = fopen(filename, io_write);
	format(line, sizeof(line), "Created=%d\r\n", DealershipCreated[dealerid]); fwrite(handle, line);
	format(line, sizeof(line), "Pos=%.3f,%.3f,%.3f\r\n", DealershipPos[dealerid][0],
		DealershipPos[dealerid][1], DealershipPos[dealerid][2]);
	fwrite(handle, line);
	fclose(handle);
}

UpdateDealership(dealerid, removeold)
{
	if(DealershipCreated[dealerid])
	{
		if(removeold)
		{
			Delete3DTextLabel(DealershipLabel[dealerid]);
		}
		new labeltext[32];
		format(labeltext, sizeof(labeltext), "Vehicle Dealership\nID: %d", dealerid);
		DealershipLabel[dealerid] = Create3DTextLabel(labeltext, 0xBB7700DD, DealershipPos[dealerid][0],
			DealershipPos[dealerid][1], DealershipPos[dealerid][2]+0.5, 20.0, 0);
	}
}

IsValidDealership(dealerid)
{
	if(dealerid < 1 || dealerid >= MAX_DEALERSHIPS) return 0;
	if(DealershipCreated[dealerid]) return 1;
	return 0;
}

LoadFuelStations()
{
	new File:handle, count;
	new filename[64], line[256], s, key[64];
	for(new i=1; i < MAX_FUEL_STATIONS; i++)
	{
		format(filename, sizeof(filename), FUEL_STATION_FILE_PATH "f%d.ini", i);
		if(!fexist(filename)) continue;
		handle = fopen(filename, io_read);
		while(fread(handle, line))
		{
			StripNL(line);
			s = strfind(line, "=");
			if(!line[0] || s < 1) continue;
			strmid(key, line, 0, s++);
			if(strcmp(key, "Created") == 0) FuelStationCreated[i] = strval(line[s]);
			else if(strcmp(key, "Pos") == 0) sscanf(line[s], "p<,>fff", FuelStationPos[i][0],
				FuelStationPos[i][1], FuelStationPos[i][2]);
		}
		fclose(handle);
		if(FuelStationCreated[i]) count++;
	}
	printf("  Loaded %d fuel stations", count);
}

SaveFuelStation(stationid)
{
	new filename[64], line[256];
	format(filename, sizeof(filename), FUEL_STATION_FILE_PATH "f%d.ini", stationid);
	new File:handle = fopen(filename, io_write);
	format(line, sizeof(line), "Created=%d\r\n", FuelStationCreated[stationid]); fwrite(handle, line);
	format(line, sizeof(line), "Pos=%.3f,%.3f,%.3f\r\n", FuelStationPos[stationid][0],
		FuelStationPos[stationid][1], FuelStationPos[stationid][2]);
	fwrite(handle, line);
	fclose(handle);
}

UpdateFuelStation(stationid, removeold)
{
	if(FuelStationCreated[stationid])
	{
		if(removeold)
		{
			Delete3DTextLabel(FuelStationLabel[stationid]);
		}
		new labeltext[32];
		format(labeltext, sizeof(labeltext), ""COL_BROWN"Gas Station\n"COL_WHITE"/refuel", stationid);
		FuelStationLabel[stationid] = Create3DTextLabel(labeltext, 0x00BBFFDD, FuelStationPos[stationid][0],
			FuelStationPos[stationid][1], FuelStationPos[stationid][2]+0.5, 20.0, 0);
	}
}

IsValidFuelStation(stationid)
{
	if(stationid < 1 || stationid >= MAX_FUEL_STATIONS) return 0;
	if(FuelStationCreated[stationid]) return 1;
	return 0;
}

forward IsPlayerInsideAHouse(playerid);
public IsPlayerInsideAHouse(playerid)
{
    if(!GetPlayerInterior(playerid)) // He is outside any house ( interior = 0)
    {
        return 1;
	}
}

public MainTimer()
{
	new string[128];
	new Float:x, Float:y, Float:z;

	for(new i=0; i < MAX_PLAYERS; i++)
	{
		if(IsPlayerConnected(i))
		{
			if(GetPlayerState(i) == PLAYER_STATE_DRIVER)
			{
				new vehicleid = GetPlayerVehicleID(i);
				if(!IsBicycle(vehicleid) && Fuel[vehicleid] > 0)
				{
					Fuel[vehicleid] -= GetPlayerSpeed(i)/1000.0;
					if(Fuel[vehicleid] <= 0)
					{
						ToggleEngine(vehicleid, VEHICLE_PARAMS_OFF);
						GameTextForPlayer(i, "~r~out of fuel", 3000, 3);
						SendClientMessage(i, COLOR_LIGHTRED, "This vehicle is out of fuel!");
					}
				}
			}
			if(RefuelTime[i] > 0 && GetPVarInt(i, "FuelStation"))
			{
				new vehicleid = GetPlayerVehicleID(i);
				Fuel[vehicleid] += 2.0;
				RefuelTime[i]--;
				if(RefuelTime[i] == 0)
				{
					if(Fuel[vehicleid] >= 100.0) Fuel[vehicleid] = 100.0;
					new stationid = GetPVarInt(i, "FuelStation");
					new cost = floatround(Fuel[vehicleid]-GetPVarFloat(i, "Fuel"))*FUEL_PRICE;
					if(GetPlayerState(i) != PLAYER_STATE_DRIVER || Fuel[vehicleid] >= 100.0 || GetPlayerMoney(i) < cost
					|| !IsPlayerInRangeOfPoint(i, 10.0, FuelStationPos[stationid][0], FuelStationPos[stationid][1], FuelStationPos[stationid][2]))
					{
						if(GetPlayerMoney(i) < cost) cost = GetPlayerMoney(i);
						GivePlayerCash(i, -cost);
						format(string, sizeof(string), "~r~-$%d", cost);
						GameTextForPlayer(i, string, 2000, 3);
						format(string, sizeof(string), "You have paid $%d for the fuel.", cost);
						SendClientMessage(i, COLOR_GOLD, string);
						SetPVarInt(i, "FuelStation", 0);
						SetPVarFloat(i, "Fuel", 0.0);
					}
					else
					{
						RefuelTime[i] = 5;
						format(string, sizeof(string), "~w~refueling...~n~~r~-$%d", cost);
						GameTextForPlayer(i, string, 2000, 3);
					}
				}
			}
			if(TrackCar[i])
			{
				GetVehiclePos(TrackCar[i], x, y, z);
				SetPlayerCheckpoint(i, x, y, z, 3);
			}
		}
	}
}

public Speedometer()
{
	new vehicleid, Float:health;
	new fstring[32], string[512];

	for(new i=0; i < MAX_PLAYERS; i++)
	{
		if(IsPlayerConnected(i) && IsPlayerInAnyVehicle(i))
		{
			vehicleid = GetPlayerVehicleID(i);
			GetVehicleHealth(vehicleid, health);
			GetVehicleParamsEx(vehicleid, engine, lights, alarm, doors, bonnet, boot, objective);

			string = "~b~~h~vehicle: ~w~";
			strcat(string, VehicleNames[GetVehicleModel(vehicleid)-400], sizeof(string));

			strcat(string, "~n~~b~~h~gps: ~w~", sizeof(string));
			strcat(string, GetPlayer3DZone(i), sizeof(string));

			strcat(string, "~n~~b~~h~health: ~g~", sizeof(string));
			fstring = "iiiiiiiiii";
			if(health > 1000.0) strins(fstring, "~r~", 10, sizeof(fstring));
			else if(health < 0.0) strins(fstring, "~r~", 0, sizeof(fstring));
			else strins(fstring, "~r~", floatround(health/100.0), sizeof(fstring));
			strcat(string, fstring, sizeof(string));

			strcat(string, "        ~b~~h~fuel: ~g~", sizeof(string));
			fstring = "iiiiiiiiii";
			if(Fuel[vehicleid] > 100.0) strins(fstring, "~r~", 10, sizeof(fstring));
			else if(Fuel[vehicleid] < 0.0) strins(fstring, "~r~", 0, sizeof(fstring));
			else strins(fstring, "~r~", floatround(Fuel[vehicleid]/10.0), sizeof(fstring));
			strcat(string, fstring, sizeof(string));

			strcat(string, "        ~b~~h~", sizeof(string));
			if(GetPVarInt(i, "Speedo")) format(fstring,sizeof(fstring),"mph: ~w~%d", GetPlayerSpeed(i, false));
			else format(fstring,sizeof(fstring),"kph: ~w~%d", GetPlayerSpeed(i, true));
			strcat(string, fstring, sizeof(string));

			strcat(string, "~n~~b~~h~engine: ", sizeof(string));
			if(engine == 1) strcat(string, "~g~on", sizeof(string));
			else strcat(string, "~r~off", sizeof(string));

			strcat(string, "        ~b~~h~alarm: ", sizeof(string));
			if(VehicleSecurity[vehicleid] == 1) strcat(string, "~g~on", sizeof(string));
			else strcat(string, "~r~off", sizeof(string));

			strcat(string, "        ~b~~h~doors: ", sizeof(string));
			if(doors == 1) strcat(string, "~r~locked", sizeof(string));
			else strcat(string, "~g~unlocked", sizeof(string));

			TextDrawSetString(SpeedoText[i], string);
		}
	}
}

public SaveTimer()
{
	SaveVehicleIndex++;
	if(SaveVehicleIndex >= MAX_DVEHICLES) SaveVehicleIndex = 1;
	if(IsValidVehicle(SaveVehicleIndex)) SaveVehicle(SaveVehicleIndex);
}

public StopAlarm(vehicleid)
{
	ToggleAlarm(vehicleid, VEHICLE_PARAMS_OFF);
}

/*forward GetVehicleIDFromPlate(Plate[]);
public GetVehicleIDFromPlate(Plate[])
{
    for(new i=1; i < MAX_DVEHICLES; i++)
    {
        if(VehicleCreated[i] == VEHICLE_PLAYER && strcmp(VehicleNumberPlate[i], Plate) == 0)
        {
            return i;
        }
    }
    return 0;
}*/

stock RandomSet(...) return getarg(random(numargs()));

public OnVehicleMod(playerid, vehicleid, componentid)
{
	new id = GetVehicleID(vehicleid);
	if(IsValidVehicle(id))
	{
		VehicleMods[id][GetVehicleComponentType(componentid)] = componentid;
		SaveVehicle(id);
	}
	return 1;
}

public OnVehiclePaintjob(playerid, vehicleid, paintjobid)
{
	new id = GetVehicleID(vehicleid);
	if(IsValidVehicle(id))
	{
		VehiclePaintjob[id] = paintjobid;
		SaveVehicle(id);
	}
	return 1;
}

public OnVehicleRespray(playerid, vehicleid, color1, color2)
{
	new id = GetVehicleID(vehicleid);
	if(IsValidVehicle(id))
	{
		VehicleColor[id][0] = color1;
		VehicleColor[id][1] = color2;
		SaveVehicle(id);
	}
	return 1;
}

ShowDialog(playerid, dialogid)
{
	switch(dialogid)
	{
		case DIALOG_VEHICLE:
		{
			new vehicleid = GetPVarInt(playerid, "DialogValue1");
			new caption[32], info[256];
			format(caption, sizeof(caption), "Vehicle ID %d", vehicleid);
			strcat(info, "Engine\nLights\nHood\nTrunk", sizeof(info));
			strcat(info, "\nFill Tank", sizeof(info));
			if(GetPlayerVehicleAccess(playerid, vehicleid) >= 2)
			{
				new value = VehicleValue[vehicleid]/2;
				format(info, sizeof(info), "%s\nSell Vehicle  ($%d)\nPark Vehicle\nEdit License Plate", info, value);
			}
			ShowPlayerDialog(playerid, dialogid, DIALOG_STYLE_LIST, caption, info, "Select", "Cancel");
		}
		case DIALOG_VEHICLE_BUY:
		{
			new vehicleid = GetPVarInt(playerid, "DialogValue1");
			new caption[32], info[256];
			format(caption, sizeof(caption), "Vehicle ID %d", vehicleid);
			format(info, sizeof(info), "This vehicle is for sale ($%d)\nWould you like to buy it?", VehicleValue[vehicleid]);
			ShowPlayerDialog(playerid, dialogid, DIALOG_STYLE_MSGBOX, caption, info, "Yes", "No");
		}
		case DIALOG_VEHICLE_SELL:
		{
			new targetid = GetPVarInt(playerid, "DialogValue1");
			new id = GetPVarInt(playerid, "DialogValue2");
			new price = GetPVarInt(playerid, "DialogValue3");
			new info[256];
			format(info, sizeof(info), "%s (%d) wants to sell you a %s for $%d.", PlayerName(targetid), targetid,
				VehicleNames[VehicleModel[id]-400], price);
			strcat(info, "\n\nWould you like to buy?", sizeof(info));
			ShowPlayerDialog(playerid, dialogid, DIALOG_STYLE_MSGBOX, "Buy Vehicle", info, "Yes", "No");
		}
		case DIALOG_TRUNK:
		{
			new vehicleid = GetPVarInt(playerid, "DialogValue1");
			new name[32], info[256];
			for(new i=0; i < sizeof(VehicleTrunk[]); i++)
			{
				if(VehicleTrunk[vehicleid][i][1] > 0)
				{
					GetWeaponName(VehicleTrunk[vehicleid][i][0], name, sizeof(name));
					format(info, sizeof(info), "%s%d. %s (%d)\n", info, i+1, name, VehicleTrunk[vehicleid][i][1]);
				}
				else
				{
					format(info, sizeof(info), "%s%d. Empty\n", info, i+1);
				}
			}
			ShowPlayerDialog(playerid, dialogid, DIALOG_STYLE_LIST, "Trunk", info, "Select", "Cancel");
		}
		case DIALOG_TRUNK_ACTION:
		{
			new info[128];
			strcat(info, "Put Into Trunk\nTake From Trunk", sizeof(info));
			ShowPlayerDialog(playerid, dialogid, DIALOG_STYLE_LIST, "Trunk", info, "Select", "Cancel");
		}
		case DIALOG_VEHICLE_PLATE:
		{
			ShowPlayerDialog(playerid, dialogid, DIALOG_STYLE_INPUT, "Edit License Plate", "Enter new license plate:", "Change", "Back");
		}
		case DIALOG_FUEL:
		{
			new info[128];
			strcat(info, "Refuel Vehicle  ($" #FUEL_PRICE " per liter)\nBuy Gas Can  ($" #GAS_CAN_PRICE ")", sizeof(info));
			ShowPlayerDialog(playerid, dialogid, DIALOG_STYLE_LIST, "Fuel Station", info, "OK", "Cancel");
		}
		case DIALOG_EDITVEHICLE:
		{
			new vehicleid = GetPVarInt(playerid, "DialogValue1");
			new caption[32], info[256];
			format(caption, sizeof(caption), "Edit Vehicle ID %d", vehicleid);
			format(info, sizeof(info), "1. Value: [$%d]\n2. Model: [%d (%s)]\n3. Colors: [%d]  [%d]\n4. License Plate: [%s]",
				VehicleValue[vehicleid], VehicleModel[vehicleid], VehicleNames[VehicleModel[vehicleid]-400],
				VehicleColor[vehicleid][0], VehicleColor[vehicleid][1], VehicleNumberPlate[vehicleid]);
			strcat(info, "\n5. Delete Vehicle\n6. Park Vehicle\n7. Go To Vehicle", sizeof(info));
			strcat(info, "\n\nEnter: [nr] [value1] [value2]", sizeof(info));
			ShowPlayerDialog(playerid, dialogid, DIALOG_STYLE_INPUT, caption, info, "OK", "Cancel");
		}
	}
}

forward OnPlayerCommandPerformed(playerid, cmdtext[], success);

public OnPlayerCommandPerformed(playerid, cmdtext[], success)
{
    if(!success) SendClientMessage(playerid, COLOR_LIGHTRED, "This command does not exist, /commands.");
    return 1;
}
