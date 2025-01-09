# RTA

The RTA file contains geometry information of barcelona city.

## Gathering tool

This data source comes in the format of an GPKG file.

#### RUN import application

To run the import application, execute the python script with the following parameters:

```bash
python3 -m gather -so postal_codes_bcn -f <file> -n <namespace> -u <user_importing> -tz <file_timezone> -st <storage>
```

## Raw Data Format

The data imported will be stored in the Hbase table, each endpoint that provides a different kind of information will
have its own row key, that will be generated as follows:

#### RTA

````json
{
  "type": "Feature",
  "properties": {
    "CFSAUID": "H0M",
    "PRUID": "24",
    "PRNAME": "Quebec / Qu\u00e9bec"
  },
  "geometry": {
    "type": "MultiPolygon",
    "coordinates": "[[[-74.51960065509294, 45.034633531104824], [-74.5193878539493, 45.03427255626563], [-74.51935443096492, 45.033714304199314], [-74.51900477328688, 45.03301969727996], [-74.51837653051162, 45.03224288287073], [-74.51794704244526, 45.0319890074028], [-74.51718793536078, 45.03167974530168], [-74.5167191720911, 45.03156972867218], [-74.51644216702975, 45.03129851287119], [-74.51615148174194, 45.03114424933773], [-74.51586116311876, 45.03094497209961], [-74.5158262835198, 45.0309074011016], [-74.51555925887628, 45.030619634029655], [-74.51543475021388, 45.03033103575394], [-74.51514665851721, 45.02987071385804], [-74.51515015168478, 45.029456640095624], [-74.51537048949905, 45.02891747693162], [-74.51564573106097, 45.0278924371768], [-74.51578814424822, 45.02755996181526], [-74.51585419690755, 45.02725416833171], [-74.51597057194509, 45.02700260351216], [-74.51620116334912, 45.02675154988412], [-74.51688119211121, 45.025890225684776], [-74.51693303835505, 45.02576441960854], [-74.51708632430474, 45.02564805698964], [-74.51757041281354, 45.02544306802036], [-74.51850945532959, 45.025474020940436], [-74.518929998434, 45.025277755759404], [-74.5203177465846, 45.0247794943277], [-74.52071304598007, 45.024565096518415], [-74.52099407644363, 45.024350234205365], [-74.52188730519558, 45.0237868616112], [-74.52200316926968, 45.02358930945588], [-74.52261646525648, 45.023105768794984], [-74.52347074819139, 45.022641233053214], [-74.52404368731086, 45.02242757745487], [-74.52501183682868, 45.02200852288932], [-74.52580051781604, 45.021795760955946], [-74.52689629962043, 45.02128719967789], [-74.52701044825884, 45.02129666021531], [-74.52727847725434, 45.02111773434549], [-74.5277502256668, 45.020858625947554], [-74.52833554095149, 45.02068102064849], [-74.52875473394876, 45.0206377317791], [-74.52911084789041, 45.02054918777603], [-74.52992563238627, 45.02024648155205], [-74.53019385567762, 45.02004053657199], [-74.53069452031532, 45.01934944675102], [-74.53076165157195, 45.01889962435664], [-74.53076399087206, 45.01861158324016], [-74.53063861986597, 45.01842202322485], [-74.53060218655358, 45.01822382866419], [-74.53053946009567, 45.018133566733184], [-74.53016612442744, 45.01722282582145], [-74.5300406858584, 45.01704227789426], [-74.5298917371913, 45.01663657815277], [-74.52955383079099, 45.01605006874913], [-74.52945303501602, 45.01560358851542], [-74.52950719060634, 45.015586512065916], [-74.52958763505916, 45.01556806169376], [-74.52975992931333, 45.01558172874197], [-74.53027991117477, 45.015609514120456], [-74.53057393302049, 45.015492081340035], [-74.53062262616638, 45.01514396289868], [-74.53077933452929, 45.01483612566883], [-74.53099543369365, 45.01448984183383], [-74.53108081445916, 45.01404860848392], [-74.53123005522231, 45.01340033796491], [-74.53144878341992, 45.01309223142518], [-74.53188534090874, 45.013084660262074], [-74.53254056936335, 45.01319571564755], [-74.53290784857225, 45.013161837314094], [-74.53313455520663, 45.01296826852394], [-74.53317765677666, 45.01265672738904], [-74.5332033812043, 45.012366852375656], [-74.53331566281344, 45.011924687987886], [-74.53359784526555, 45.01179233836056], [-74.53420670620802, 45.011818888025175], [-74.53497540018024, 45.01177670082999], [-74.53525299400908, 45.01165597959653], [-74.53537692741705, 45.01149855609776], [-74.53526880247207, 45.011301380762454], [-74.53489913725807, 45.01118418449583], [-74.53425770025734, 45.01103819840486], [-74.53387101386465, 45.01098665613989], [-74.53379472100207, 45.010820898105656], [-74.53385364903083, 45.01058155756097], [-74.53408200452178, 45.010451080848355], [-74.53444259201989, 45.01032173210623], [-74.53566673749677, 45.010156431277366], [-74.53615563441721, 45.009970909578506], [-74.53623251084589, 45.00964098694639], [-74.53608394135642, 45.00936676573841], [-74.53597341202608, 45.009018510732005], [-74.53603569738124, 45.00847857634463], [-74.5359421677135, 45.00806463405523], [-74.53564879093855, 45.00768640691467], [-74.53556289640585, 45.00691627972903], [-74.53561851948385, 45.00670764401723], [-74.53587640671022, 45.00661443027708], [-74.53623481790744, 45.00664779737052], [-74.53648037237845, 45.00676552745223], [-74.53696310526851, 45.00711222487001], [-74.53736171440741, 45.007335589873755], [-74.537598732241, 45.0074076762077], [-74.53784721153129, 45.007433100445446], [-74.53950970803466, 45.00741281320424], [-74.53968763525033, 45.0073775219229], [-74.5398151697388, 45.007297007309674], [-74.5398794991374, 45.00718924808234], [-74.54002021018081, 45.00704577795826], [-74.54011069659445, 45.00683909348578], [-74.54017444400286, 45.00680334507773], [-74.54036793817743, 45.006408043193304], [-74.54051195737287, 45.00585050103578], [-74.54066581041315, 45.005653069531384], [-74.5410874331595, 45.00529471313486], [-74.54217871262573, 45.00529007112265], [-74.5423940531921, 45.005335941654096], [-74.54287458706735, 45.00554491926816], [-74.54315394847104, 45.005519017128634], [-74.54330693777834, 45.0054296124315], [-74.54346026340329, 45.005295199866026], [-74.5434866417515, 45.00516929608035], [-74.542765542421, 45.00489633618844], [-74.5426397499725, 45.004760823615385], [-74.54260297427392, 45.00459863582234], [-74.54268023674523, 45.00445489920508], [-74.54354327665615, 45.00443136071825], [-74.54372132170681, 45.0043780637704], [-74.54388721183054, 45.0042616997243], [-74.54392656520514, 45.004099826368915], [-74.54376183514393, 45.00407214621302], [-74.54336855389442, 45.00406157082461], [-74.54326813137877, 45.00392615396532], [-74.54321032743248, 45.00321476639044], [-74.54330092452221, 45.00299008431337], [-74.54339047535404, 45.00290041703729], [-74.54358165840723, 45.002793159778825], [-74.54396300544309, 45.002704665098136], [-74.54401475912545, 45.00257883243558], [-74.54400729884587, 45.001921687122554], [-74.54405990068084, 45.001687825640005], [-74.5442144306482, 45.00140038488528], [-74.5444429586502, 45.00138330223337], [-74.54483615542892, 45.00140285954195], [-74.54498874815155, 45.00135847804899], [-74.54504070055341, 45.00120563661091], [-74.54500351285017, 45.001097470290055], [-74.54479045781181, 45.00076354032739], [-74.54471605015729, 45.000547201194216], [-74.54455287692814, 45.00032151215076], [-74.54441995354527, 45.000050919024865], [-74.54441551385953, 45.000041906224936], [-74.5443403317774, 44.999924584801626], [-74.54434253152773, 44.9996455307762], [-74.54444433303699, 44.999609924910544], [-74.54512895639456, 44.99967565750491], [-74.54526871020252, 44.99964922333137], [-74.545435221913, 44.99945183955023], [-74.5455647131904, 44.99911927501239], [-74.54563074220306, 44.99879546678611], [-74.54559378472626, 44.99865129984883], [-74.54560389013967, 44.99829426936711], [-74.55882746828173, 44.99884660721427], [-74.60082656094032, 44.99914119944832], [-74.60171841435485, 44.99917157734667], [-74.60214710773447, 44.99929021739645], [-74.60475356225862, 44.99930962127824], [-74.60514064023876, 44.99919729507502], [-74.61420173137536, 44.9993557762536], [-74.62535527018264, 44.999426205513444], [-74.63718832358703, 44.99930904999933], [-74.63754020216781, 44.999319740641894], [-74.63740195906234, 44.99942976502127], [-74.63739634271239, 44.99942975990165], [-74.6372434916846, 44.99951930901737], [-74.6368737543133, 44.99980618971944], [-74.63678385742352, 44.99997693133291], [-74.63664376494856, 45.00008638146737], [-74.63655435390959, 45.00015625180347], [-74.63584144503204, 45.00053205301068], [-74.63558602691586, 45.00079228592553], [-74.6353683329837, 45.001106660042765], [-74.63515166851536, 45.001259006232495], [-74.63455465587437, 45.00136512097147], [-74.63422483389269, 45.00135507011057], [-74.63398399222424, 45.0013182837418], [-74.63360483549754, 45.001083011861425], [-74.63341480011204, 45.00103740577993], [-74.63285647309887, 45.001044603926246], [-74.63218342663784, 45.00113246674374], [-74.63176463533526, 45.001149115083074], [-74.63114310909776, 45.00112011245637], [-74.63068645401337, 45.00110062789712], [-74.63036948796886, 45.00106359197165], [-74.6300777825243, 45.00104464696953], [-74.6292781707306, 45.00108705907316], [-74.62915079902386, 45.001158673855734], [-74.62893478324776, 45.00121197566496], [-74.62883262569753, 45.00131066926197], [-74.62881929810497, 45.00140964267413], [-74.62869048391113, 45.001706283272355], [-74.62797770719315, 45.0020550289156], [-74.62754600671272, 45.002098645834344], [-74.62730511203434, 45.002070852566156], [-74.6268629429241, 45.00177234881637], [-74.62659697998589, 45.00169945827278], [-74.62649549157058, 45.00169911984529], [-74.6261011412753, 45.00185085572449], [-74.62570612507699, 45.00211064438983], [-74.62538838760406, 45.002190594168745], [-74.6251598409544, 45.00221687004795], [-74.62458556460886, 45.00271908136247], [-74.62433098490182, 45.00284426529395], [-74.62337960039136, 45.00280514445118], [-74.62277056747612, 45.002803125334964], [-74.62263116278484, 45.002775662064145], [-74.62259344958585, 45.00272151472569], [-74.62067705979233, 45.00278717518533], [-74.61994042180645, 45.00289276046701], [-74.61962329350749, 45.002882695560196], [-74.6194585215736, 45.002855154657965], [-74.61916655990497, 45.002872187731725], [-74.61855567277642, 45.00314920383671], [-74.6181602582219, 45.00346294846526], [-74.61790540631598, 45.00362412844402], [-74.61754971073904, 45.00368594640718], [-74.61744820834724, 45.003685622007986], [-74.61743535625315, 45.003712567040566], [-74.61733271038412, 45.00388325889728], [-74.61687350720506, 45.004241806260815], [-74.61661894460346, 45.00435798223837], [-74.61641499426133, 45.00450132104219], [-74.61618473258885, 45.0047796064176], [-74.61605560840604, 45.005112254325475], [-74.6158248000048, 45.00547153048271], [-74.61576015060052, 45.00565137164349], [-74.61534966766453, 45.006316121641255], [-74.61529747509059, 45.006531993538864], [-74.6152699057486, 45.00685595837251], [-74.61527815708307, 45.00752213844257], [-74.61523953056653, 45.00760304022882], [-74.61522436344116, 45.00797204870067], [-74.61512183814813, 45.00812474958937], [-74.6150174118423, 45.00855649011959], [-74.61465837593639, 45.00911339816937], [-74.61409561593995, 45.00976863441881], [-74.61380238006421, 45.009974677094], [-74.61340637456398, 45.010360416178706], [-74.61255317728435, 45.01079862006479], [-74.6121195284444, 45.01112122080706], [-74.61169996335516, 45.01123681674384], [-74.61155951391528, 45.0113623653554], [-74.61104929630699, 45.011747706868675], [-74.61037390741335, 45.01215950147672], [-74.60974852849523, 45.012679471276364], [-74.60941701026907, 45.01291239626393], [-74.60907197310895, 45.01326228824989], [-74.60856151332085, 45.01367462283087], [-74.60770596339016, 45.014445862389614], [-74.60745006543114, 45.0147510483091], [-74.60728411965277, 45.01489449082475], [-74.60692572008368, 45.01533436688509], [-74.6065941772576, 45.01556725993227], [-74.6061472593552, 45.01596181143981], [-74.60564985014524, 45.01632016783317], [-74.60530495917666, 45.01664304657367], [-74.60473247862905, 45.01683911611123], [-74.60461771389399, 45.01691973728287], [-74.60454087879206, 45.0170184940148], [-74.60443921318463, 45.01703612304045], [-74.60412102198309, 45.01717005606592], [-74.60409507281364, 45.01725099861524], [-74.60366213617282, 45.01745653214328], [-74.60331784560341, 45.017689397660504], [-74.60320282366713, 45.01780600916288], [-74.60261702296923, 45.018092038324426], [-74.60189260434059, 45.01823355466083], [-74.60085212018487, 45.01819389895358], [-74.60082700658856, 45.01815780468235], [-74.60045902025405, 45.01814751519241], [-74.60053703935282, 45.0178777274424], [-74.60049944063707, 45.01780559205903], [-74.60004358341475, 45.01765996441312], [-74.5998279302992, 45.017641209731394], [-74.5993980508476, 45.017405643311015], [-74.59917005318681, 45.01734182335878], [-74.59895449642269, 45.01731406159517], [-74.59878924781533, 45.017349508013915], [-74.59871272503477, 45.01740323202602], [-74.59871133957053, 45.0176012699515], [-74.59859656212025, 45.01768188374152], [-74.59819087427118, 45.017617448149295], [-74.59767014214417, 45.01766963940064], [-74.59747932695176, 45.017731960192094], [-74.59732709913531, 45.01772244322609], [-74.5966403397575, 45.01791804751985], [-74.59643737580586, 45.01790832191401], [-74.59640106747148, 45.01765614601042], [-74.59631290322886, 45.01755681497625], [-74.59613554195687, 45.017511169448724], [-74.59591939939209, 45.01756442007426], [-74.59485299473523, 45.017605666249274], [-74.59442022052103, 45.01778415114631], [-74.59414000685989, 45.01792720858509], [-74.5939492985078, 45.017971522614616], [-74.59377085201018, 45.01807890697645], [-74.59357995895017, 45.01815025577964], [-74.59352871794191, 45.018222086076065], [-74.59334999957116, 45.0183654859964], [-74.5933233354418, 45.01854542088596], [-74.59325879585688, 45.018698227779915], [-74.59308017046199, 45.01883262237954], [-74.5929904875601, 45.01894932597201], [-74.59262015164249, 45.01927206202947], [-74.59240355097629, 45.01938833225813], [-74.592238237662, 45.019432754478416], [-74.59209886172665, 45.01939622977623], [-74.5919591357918, 45.01941372748408], [-74.5917297743987, 45.01953894007512], [-74.5913996783805, 45.019555773277716], [-74.59119672612202, 45.01953704143521], [-74.59077859778053, 45.01943651156912], [-74.59015683373303, 45.019416296479854], [-74.5897503155061, 45.01946884136053], [-74.58955992165842, 45.0194681424124], [-74.5894966698938, 45.01944093144831], [-74.58945914959806, 45.019359779062086], [-74.58943614941026, 45.019026615660685], [-74.58938595775392, 45.01894542618972], [-74.58904393523026, 45.018854175275365], [-74.58887944971531, 45.01878157235497], [-74.58829595669617, 45.01873445868548], [-74.5879783595916, 45.018778327881016], [-74.58716594980997, 45.01879338136632], [-74.58701339258461, 45.01882885067133], [-74.58700024306174, 45.01889180950623], [-74.5868721664299, 45.01905339131495], [-74.58684580411199, 45.01918832091428], [-74.58673085145163, 45.01928691270603], [-74.58611969908046, 45.019554761364475], [-74.5859162411999, 45.019608032830064], [-74.58564959591058, 45.01962507822463], [-74.58523081012079, 45.01961455471262], [-74.58514231788985, 45.01956921008185], [-74.5849648340618, 45.01954156580763], [-74.58472440697514, 45.0194416718263], [-74.58426793249696, 45.019377000752755], [-74.58412871415358, 45.019322471015656], [-74.58378602753217, 45.01932123201904], [-74.58322660885183, 45.019454214907356], [-74.58318789523348, 45.01954410162643], [-74.58293385788393, 45.01957018893553], [-74.58266649332474, 45.019686220950675], [-74.58236179078901, 45.01969410976619], [-74.58203129374566, 45.01976492434666], [-74.58181545687705, 45.0197731375057], [-74.58152249403037, 45.01991608737732], [-74.58133178962069, 45.019960406081545], [-74.58126788428997, 45.02002317294351], [-74.58098871006268, 45.02001314800331], [-74.58060691043326, 45.02015577443966], [-74.58036535822627, 45.020208904430895], [-74.58009870728894, 45.020225933368124], [-74.5797691834954, 45.02016169648459], [-74.57947791874109, 45.0200706008819], [-74.5793518006057, 45.01996211744205], [-74.5790982773331, 45.019916178579614], [-74.57766400484998, 45.01991988619088], [-74.57716954968002, 45.01984604347783], [-74.5765714423993, 45.020059857570516], [-74.57643191754056, 45.02005035088097], [-74.57642059549946, 45.01986127033964], [-74.5761426585926, 45.01968921387381], [-74.57577472066701, 45.01966983548649], [-74.57550883581837, 45.01957883666137], [-74.5754079865742, 45.01948843251426], [-74.57506570374788, 45.01943314441502], [-74.57467226974327, 45.019431675600416], [-74.57450658882932, 45.019521093399845], [-74.57446792284277, 45.01960196452386], [-74.57412263214762, 45.019951746281095], [-74.57397006081298, 45.01998719359717], [-74.57376665179964, 45.02003142567451], [-74.57355015413523, 45.0201296581153], [-74.57332217929358, 45.020065771654686], [-74.57272571792667, 45.02005455768834], [-74.57262390223501, 45.02009017469441], [-74.5725733318696, 45.02006299128804], [-74.57248410114299, 45.02011665399141], [-74.57212839383914, 45.0201603348424], [-74.57131662197668, 45.02008528547068], [-74.57099928658106, 45.02009307835337], [-74.57075772341408, 45.020146182408766], [-74.57062970714675, 45.020289742502314], [-74.5704253849596, 45.020460005341896], [-74.57033564021965, 45.020576687141954], [-74.56982791818653, 45.02058379117133], [-74.56968877009353, 45.020520251161834], [-74.56948682439943, 45.02036645106546], [-74.5694245951692, 45.02020418258255], [-74.56945085332113, 45.020087250120554], [-74.56983422203419, 45.019737637266054], [-74.5703060492639, 45.019442352645065], [-74.57081514434027, 45.01925520616119], [-74.571043808901, 45.01922906674211], [-74.57126002011921, 45.01916685708123], [-74.57137472843044, 45.019104277135895], [-74.5715157446368, 45.018915777115836], [-74.57149211517624, 45.01868165343915], [-74.57110016015538, 45.0184821236439], [-74.57079621781484, 45.01839095396658], [-74.5705942463967, 45.01824617645785], [-74.57018983776854, 45.01801059790802], [-74.56955655531387, 45.01783718343993], [-74.56954488554845, 45.01770212600144], [-74.569444140722, 45.01759370992512], [-74.5694829804765, 45.017494824929955], [-74.57036062793024, 45.01723707307601], [-74.57048821655714, 45.01714755487786], [-74.57062942778737, 45.016932022653975], [-74.57068121395221, 45.01679718576416], [-74.57091187087178, 45.016500989272416], [-74.57107759435468, 45.01640261630813], [-74.571548226883, 45.016260338402326], [-74.57191763822951, 45.01608169753263], [-74.57255511607018, 45.015687976055666], [-74.57297653867234, 45.01533849604197], [-74.57323270408918, 45.01502438921762], [-74.57329650209991, 45.01497960425679], [-74.5732840177065, 45.01495255400096], [-74.57315695928926, 45.01497008590068], [-74.57295303418077, 45.01508635319569], [-74.57287601169234, 45.0152030810219], [-74.57284969993981, 45.0153290235594], [-74.57245461436872, 45.015552591463674], [-74.57239041635215, 45.01565136644724], [-74.5720464768603, 45.015821114485924], [-74.57116830102821, 45.016150888425024], [-74.57098989800477, 45.016249245943094], [-74.57073540600877, 45.01633830068943], [-74.57058215561364, 45.01646374817668], [-74.57050474876232, 45.016634496506335], [-74.57047786281261, 45.01683244668562], [-74.57010759622626, 45.0171281067558], [-74.56996761450543, 45.01718159274977], [-74.5693064507709, 45.01734114459647], [-74.56924217727212, 45.017448929912426], [-74.56926607393501, 45.017647061140885], [-74.56944119109484, 45.01798977457817], [-74.56963060854441, 45.01811651519271], [-74.56989699666998, 45.018135540445705], [-74.5702134849115, 45.01824475232596], [-74.5704407009139, 45.01840764095446], [-74.57116133041397, 45.018788419527], [-74.57121142342514, 45.018878631015355], [-74.57116004586408, 45.018959453885564], [-74.57065218583931, 45.01898455509206], [-74.56967186732736, 45.01938595683122], [-74.56955649953774, 45.0195385492013], [-74.56924988131945, 45.01980744978908], [-74.56894398312473, 45.01997732302783], [-74.56891760100092, 45.02011225471811], [-74.5689799510385, 45.02025652404719], [-74.56910626820982, 45.02033801762929], [-74.56930727598105, 45.02061782574606], [-74.56945903011662, 45.020690418317514], [-74.56945900787466, 45.02069332065232], [-74.56945899742925, 45.02069332400416], [-74.56945792764994, 45.020834442697435], [-74.56940670168268, 45.020897272549185], [-74.56926701880292, 45.0209057473833], [-74.56888545439745, 45.021012332269095], [-74.5687965858021, 45.021011992967786], [-74.56861958509909, 45.02092128813501], [-74.56834037619748, 45.020920242482624], [-74.5679843116177, 45.02100891123059], [-74.56757660310532, 45.02121442362448], [-74.56738511794016, 45.02135773341506], [-74.56700272593663, 45.02157231866228], [-74.5666197916446, 45.021858918377404], [-74.56642858257922, 45.0219662341388], [-74.56581581201623, 45.022432003073774], [-74.56507747815733, 45.022717247701635], [-74.56462013134565, 45.0227695275022], [-74.56436558998996, 45.02285856683275], [-74.56399737218958, 45.02287516350045], [-74.56328528584979, 45.023043485863084], [-74.56278883364354, 45.02323061628559], [-74.56218926147686, 45.02362439447101], [-74.56183235650266, 45.023821080230604], [-74.56175522271316, 45.02394681520447], [-74.56146232928529, 45.0240717092737], [-74.56127162194875, 45.024115993002695], [-74.56111880806218, 45.02417839980557], [-74.560837581465, 45.02443838569791], [-74.56055831661757, 45.024437309002515], [-74.56025322427875, 45.02449915337795], [-74.55975654905691, 45.02471328016671], [-74.55943845855849, 45.0248110665109], [-74.5590055927642, 45.02498043651756], [-74.55883973364381, 45.02508782751928], [-74.5587370225258, 45.02524045832908], [-74.55789915480197, 45.02525521943204], [-74.55777235019028, 45.02523673743789], [-74.55765851761815, 45.025182279760536], [-74.55741756759629, 45.0251543268745], [-74.55730372608937, 45.025099893090996], [-74.55684713086639, 45.02505311175231], [-74.55675848493095, 45.02502575532357], [-74.55663178436464, 45.02499826645693], [-74.55655597421509, 45.024952958712646], [-74.55640435425285, 45.02486234303629], [-74.55623976196095, 45.02480770237576], [-74.55603653528964, 45.02482491452316], [-74.55589635077274, 45.02489637346205], [-74.55574263634902, 45.02507582432556], [-74.55550014702571, 45.02524591725864], [-74.5554102603128, 45.025380593361696], [-74.55538415978073, 45.02547051256953], [-74.55539589229289, 45.025596571299914], [-74.55524260208334, 45.025722004680894], [-74.55522878046604, 45.02586599008949], [-74.5549733891852, 45.026063021075764], [-74.55464315319799, 45.026088755971294], [-74.55440232873347, 45.02604279496234], [-74.55423717619243, 45.02606016759687], [-74.55419846820084, 45.02614103238946], [-74.55401998872604, 45.02623936065866], [-74.55370217661819, 45.02630110987928], [-74.55325823715697, 45.02625437662371], [-74.55310549906655, 45.02630778939], [-74.55295220007096, 45.02643321926523], [-74.55263417687156, 45.026522001190365], [-74.55251992497533, 45.02652152972018], [-74.55235533139509, 45.02646688152763], [-74.55165825771597, 45.026329125366345], [-74.5513292137014, 45.02620180141973], [-74.55064469098527, 45.02608208008687], [-74.55051819115018, 45.0260275703605], [-74.54981937304481, 45.026114839547546], [-74.54941177061143, 45.02629326888612], [-74.54906676528243, 45.0265799664717], [-74.54884992083767, 45.026714142158035], [-74.5486707292484, 45.02690247744462], [-74.54855657146335, 45.02689301991148], [-74.54847996303049, 45.02694672774477], [-74.54806011086856, 45.02707109106755], [-74.54735996738842, 45.02732036985832], [-74.54690264868951, 45.02736357936614], [-74.54579818811062, 45.02737718871621], [-74.5452273796698, 45.027320904046285], [-74.54488553053038, 45.02721153668127], [-74.54462016637727, 45.02705743779374], [-74.54408839956781, 45.02688426748446], [-74.54364591507982, 45.02665745863469], [-74.5432151955608, 45.0265477209273], [-74.54264545576166, 45.02636539220619], [-74.54212552427603, 45.026300296055716], [-74.54193511756515, 45.02629955146711], [-74.54160589593985, 45.026199203871684], [-74.5413531509294, 45.026054152171795], [-74.5411804950205, 45.026012559804045], [-74.5410871266848, 45.025990067466104], [-74.54096077255299, 45.0259175444074], [-74.54026401059346, 45.025743700285176], [-74.53997233316115, 45.02570651553682], [-74.53917258359984, 45.025712308957154], [-74.53871534559752, 45.0257464642751], [-74.53832116370748, 45.025834883994904], [-74.53759682689298, 45.02593099177537], [-74.5369737775676, 45.026063484795756], [-74.53621190270675, 45.02609641135039], [-74.53595831622776, 45.02605936139948], [-74.53498066269547, 45.02609139901249], [-74.53472614183949, 45.02617137458644], [-74.53454754673979, 45.02627867626114], [-74.53450880332441, 45.026359532645344], [-74.53462313719194, 45.02635099057665], [-74.53480127930648, 45.02629770598788], [-74.53541122169439, 45.02621917596689], [-74.53555082982541, 45.02621973460025], [-74.53610846220288, 45.02633002195031], [-74.53660313899933, 45.02637705685642], [-74.53686992484305, 45.02635112029949], [-74.53711159930015, 45.02628908706705], [-74.5374165277296, 45.02625433292071], [-74.53826847924137, 45.026068736889556], [-74.53863688648994, 45.02603419703438], [-74.54007166656329, 45.025985990629394], [-74.540249157728, 45.026013700185445], [-74.54079374159707, 45.02616894354562], [-74.5417670867215, 45.026676938890894], [-74.54205883387768, 45.02670513016382], [-74.54249046737418, 45.02669784407309], [-74.54300975632414, 45.02684396776574], [-74.5432624767129, 45.026989008559966], [-74.54351547409576, 45.02709802437504], [-74.5437688686178, 45.027162065304935], [-74.54402179708089, 45.02728009198376], [-74.54446334508565, 45.02762392271804], [-74.544614950339, 45.027714559726114], [-74.5455529999553, 45.02788030855416], [-74.54594638425608, 45.02789988093092], [-74.54626385918576, 45.027883139877794], [-74.54650488753143, 45.02790211089822], [-74.54691114885684, 45.027894710050404], [-74.5480172908647, 45.02767405269212], [-74.54851359302148, 45.02751397449542], [-74.54890859652562, 45.027326517428705], [-74.54971217391845, 45.02683458745239], [-74.5499039044279, 45.02666429291954], [-74.55014572723863, 45.026584231294535], [-74.55041249692255, 45.02655827879719], [-74.55075514302825, 45.026568626378776], [-74.55161736405547, 45.02668904647533], [-74.5518452912323, 45.026761953549226], [-74.55226263452107, 45.02696161813656], [-74.55260547323331, 45.026944970869415], [-74.5534951634796, 45.02680441375001], [-74.55380070142884, 45.0266885986006], [-74.55408050436175, 45.0266176721307], [-74.55430906258137, 45.02660954332815], [-74.55433381735922, 45.02669066409397], [-74.55433075198563, 45.026692812340656], [-74.55400197878014, 45.02692341261656], [-74.55358147896763, 45.02712882472394], [-74.5532360374181, 45.027478551712434], [-74.55319739573943, 45.02755040442871], [-74.55324684273707, 45.02772163516192], [-74.55306779463328, 45.02789198005715], [-74.55287653726707, 45.0279992455545], [-74.552735811405, 45.02814272528319], [-74.5521200502282, 45.02896848687748], [-74.55199268508993, 45.029021990248495], [-74.55188868782474, 45.02933665268951], [-74.55195024445524, 45.02957994641026], [-74.55206329551854, 45.02973341226544], [-74.55211310345399, 45.029859639350576], [-74.55213650870975, 45.03011178039742], [-74.5520704301576, 45.030444603558045], [-74.55172565318077, 45.03070428663075], [-74.55143370899164, 45.030703145700734], [-74.55102649551621, 45.030827592037284], [-74.55034078359407, 45.03085187904307], [-74.5498700362415, 45.03098504958846], [-74.54958899767584, 45.03120901442179], [-74.5495121221306, 45.03129872490238], [-74.54946013502615, 45.03145153453008], [-74.54878408541234, 45.03186296735437], [-74.54849196852983, 45.03187981041868], [-74.54813660718554, 45.031869410894494], [-74.54793391416884, 45.03181458610133], [-74.5475290891685, 45.03163294046268], [-74.5473527446831, 45.03146121337908], [-74.54717599945116, 45.031334485553174], [-74.54696082729532, 45.03125262714986], [-74.54670717625167, 45.0312246015003], [-74.54627634453499, 45.03112386418597], [-74.54571836393421, 45.03104963827052], [-74.5456301435395, 45.03096827596107], [-74.54479252563083, 45.03093793322332], [-74.54465236575959, 45.03100038860522], [-74.54455003455618, 45.03109898880751], [-74.54434636768838, 45.031170200238314], [-74.54405444794898, 45.031160040506435], [-74.5439389361381, 45.031321602942015], [-74.54360930205043, 45.03126626662477], [-74.54294931704723, 45.03124563387028], [-74.54259244509328, 45.03142423203119], [-74.5423005584058, 45.03141407337305], [-74.54210976685667, 45.03145831103891], [-74.5419059609801, 45.03154751738658], [-74.54167700224558, 45.031600621016565], [-74.54117921410896, 45.03194067893082], [-74.54106351216859, 45.03212025618703], [-74.54101200339231, 45.03221005467967], [-74.54092005228186, 45.03259677916661], [-74.54054413061435, 45.033567467551705], [-74.54045455717194, 45.03365712707582], [-74.54007155458812, 45.03392564235412], [-74.53971498132654, 45.034059242015886], [-74.53951085552626, 45.034184438316416], [-74.53939377968048, 45.03453504379921], [-74.5391876434356, 45.034912276575746], [-74.53881715452589, 45.03519885738546], [-74.53826881038376, 45.035502687821044], [-74.53800183610409, 45.03554663029092], [-74.53726588145634, 45.035498637136826], [-74.53708866971259, 45.03543490156056], [-74.53697527737732, 45.03532641988041], [-74.53660562910888, 45.03550497045117], [-74.53643924189389, 45.03567532220704], [-74.53641223902808, 45.03587326186119], [-74.53625821070992, 45.03607967728106], [-74.53606656849149, 45.036231931709175], [-74.53583535368371, 45.03656404930012], [-74.53570701468803, 45.03673456608634], [-74.53561763426681, 45.03679720873437], [-74.53531300323499, 45.03678697546343], [-74.53507205892672, 45.0367499971804], [-74.53481903733542, 45.036640928393496], [-74.53460462297168, 45.036469023827514], [-74.5343278705633, 45.03615282566266], [-74.53424024160327, 45.03599945422861], [-74.5341798014873, 45.035621123873106], [-74.53409139271771, 45.035566737377515], [-74.53382742369632, 45.03524160269496], [-74.53352477902789, 45.034988314394], [-74.5317863351309, 45.03488217075588], [-74.53111313902237, 45.03492441950579], [-74.53046566903129, 45.03492177181168], [-74.53012247537117, 45.03497436061809], [-74.52986907601732, 45.03491028379952], [-74.5297716292581, 45.03440581320275], [-74.5296224035113, 45.03402711802379], [-74.52923380571448, 45.033422377366406], [-74.52893768003966, 45.03237694736436], [-74.52859663508876, 45.03216850790817], [-74.52873356630003, 45.032502124984845], [-74.52878138531062, 45.03286240053897], [-74.52893172383726, 45.03310606867814], [-74.52899208218267, 45.03348439144121], [-74.52926811797775, 45.03388160988762], [-74.52927837021946, 45.03417872934423], [-74.52941366624222, 45.03471038316517], [-74.52938659331033, 45.034917339124306], [-74.5291452477874, 45.03493434709872], [-74.52875005558342, 45.03513074295593], [-74.52819155320721, 45.03511944534808], [-74.52788546529568, 45.03528920399429], [-74.5261975631895, 45.03521021111494], [-74.52538397624559, 45.03534186443162], [-74.5253332427298, 45.03533264635084], [-74.52495070053129, 45.03553809818519], [-74.5246466862709, 45.035455808620554], [-74.52436786446505, 45.03541296871846], [-74.52392394585274, 45.03534476912404], [-74.5238481415297, 45.03529945589942], [-74.52372139787666, 45.03527191244862], [-74.52313743271276, 45.03526949599187], [-74.5227950435925, 45.035223048025856], [-74.52235196535561, 45.035068169810245], [-74.52180639317424, 45.03502987290053], [-74.52101835731904, 45.03513459134261], [-74.52096690567508, 45.03521539822252], [-74.52089043615852, 45.03525106636844], [-74.52043386699137, 45.0351951405065], [-74.51984028217969, 45.03482357839838], [-74.51960065509294, 45.034633531104824]]] [[[-74.64125285816597, 45.00154839336718], [-74.64146917831175, 45.00145004382314], [-74.64153347057574, 45.00131521905215], [-74.64181320719727, 45.001217087084704], [-74.64198022407206, 45.00088454213647], [-74.64208247980383, 45.00076784260275], [-74.64228765509424, 45.000417402732566], [-74.64228793729063, 45.00037237822451], [-74.64239033587815, 45.00022866953112], [-74.64234642432753, 45.00008546216777], [-74.64234058270223, 45.000066478878004], [-74.64234171708999, 44.999886460861205], [-74.64234410759889, 44.99988583027885], [-74.64242526320231, 44.99942951159293], [-74.6424322532939, 44.999390109304834], [-74.64243991530637, 44.99939017614483], [-74.64669134739489, 44.999444453550055], [-74.65007544068914, 44.99944444358734], [-74.65291830860225, 44.9994321501165], [-74.6529383433282, 44.99943223893618], [-74.65306523380622, 44.99943222518212], [-74.65319211469333, 44.999432235610136], [-74.65331899558048, 44.999432245858564], [-74.65344587646779, 44.99943225592742], [-74.65357276692892, 44.99943224149761], [-74.65369964781618, 44.99943225120732], [-74.65382649441031, 44.999432253987486], [-74.65395337529766, 44.9994322633381], [-74.6540802656987, 44.99943224817814], [-74.65420714664612, 44.9994322571814], [-74.65433402753365, 44.999432265993285], [-74.65446090842114, 44.99943227462555], [-74.6545877645453, 44.999432251955014], [-74.65471464543279, 44.999432260228154], [-74.65484152638037, 44.999432268333585], [-74.65496840726803, 44.99943227624763], [-74.65509528815566, 44.999432283982046], [-74.65522217861631, 44.999432267217664], [-74.65534902515047, 44.999432267831814], [-74.6554759060982, 44.99943227503936], [-74.655602786986, 44.99943228205557], [-74.65572967740306, 44.99943226451842], [-74.6558565583509, 44.99943227118728], [-74.65598343923865, 44.99943227766472], [-74.65611032012644, 44.99943228396259], [-74.6562371667207, 44.999432283331906], [-74.65636405712085, 44.999432264939465], [-74.65649093806879, 44.999432270710486], [-74.65661781895662, 44.999432276290115], [-74.65674469984448, 44.99943228169013], [-74.65687158073246, 44.99943228691063], [-74.65699847120908, 44.999432267589434], [-74.65712531780325, 44.99943226570209], [-74.65725219869114, 44.99943227038388], [-74.65737907957907, 44.99943227488605], [-74.65750596046709, 44.99943227920871], [-74.65763285092675, 44.99943225903222], [-74.65775973181475, 44.99943226299572], [-74.65788657840879, 44.999432260031234], [-74.65801345929682, 44.99943226363564], [-74.65814034018479, 44.999432267060406], [-74.65826723064409, 44.99943224598604], [-74.65839411153213, 44.99943224905167], [-74.65852099242007, 44.99943225193773], [-74.65864787336807, 44.99943225465605], [-74.65877471990207, 44.99943225042309], [-74.65890160085009, 44.99943225278229], [-74.6590284912657, 44.99943223057601], [-74.65915537215362, 44.99943223256425], [-74.6592822531017, 44.999432234384734], [-74.65941604670921, 44.999432232618375], [-74.65954257504245, 44.99943890387319], [-74.65966911298368, 44.9994455506299], [-74.65979564139165, 44.99945222152798], [-74.6599221698971, 44.999458892259476], [-74.66004869837987, 44.99946556280081], [-74.6601752364704, 44.99947220884396], [-74.66030173073372, 44.999478872281095], [-74.66042825932864, 44.99948554228732], [-74.66055479747102, 44.9994921877835], [-74.66068132620072, 44.99949885744481], [-74.66080785490776, 44.99950552691589], [-74.66093438371226, 44.99951219622045], [-74.6610609220039, 44.99951884100308], [-74.66118745088312, 44.99952550995087], [-74.66120961585743, 44.999526671589514], [-74.6611845588431, 44.99965584302913], [-74.66119486844899, 45.00006096198318], [-74.6611951396439, 45.000079843002], [-74.6612039417613, 45.00067312707901], [-74.66123992130036, 45.00102429733108], [-74.66118847542724, 45.00114117189564], [-74.6608702898197, 45.00131127220263], [-74.66066715953829, 45.001328657272126], [-74.66004704596794, 45.00105676431586], [-74.65968023564677, 45.00086664415773], [-74.65943968898232, 45.00077589038147], [-74.659160770525, 45.00073905183197], [-74.65877997919243, 45.000764926351806], [-74.65841163631838, 45.00082684031152], [-74.65795364328396, 45.00103251399694], [-74.65763527622053, 45.00122960516274], [-74.65696142784277, 45.00146163548262], [-74.65686019785382, 45.001416330937026], [-74.65677190279042, 45.00132602928296], [-74.65660746477504, 45.00124452763369], [-74.65641741504744, 45.00119894596033], [-74.65599860727279, 45.00121567637236], [-74.65536294765452, 45.001420806814174], [-74.65513426036861, 45.00147413712756], [-74.6546378420367, 45.0017336777442], [-74.65453569047821, 45.00184141203179], [-74.65452251716441, 45.00192236708752], [-74.65444612639672, 45.00196714801445], [-74.65401473247371, 45.00196584312694], [-74.65351863777204, 45.00217139738448], [-74.65330212800895, 45.002305765778615], [-74.65312324305866, 45.0025122594887], [-74.65276448950138, 45.003087300055846], [-74.65276264022825, 45.0033933607631], [-74.65271116977499, 45.00351023170158], [-74.6525833872304, 45.003662877853166], [-74.65240383510859, 45.00397738914174], [-74.65179281480069, 45.00429959620612], [-74.6516140887443, 45.00447908598642], [-74.65136002697169, 45.004523325694905], [-74.65111906447962, 45.00450458305805], [-74.65097986113895, 45.00444114957278], [-74.65040937525508, 45.00435837781387], [-74.65021953356738, 45.00427679257379], [-74.65001761431886, 45.00409614072537], [-74.649384684263, 45.003851144603594], [-74.64904286505715, 45.00372405942636], [-74.64861177106029, 45.003668716390564], [-74.64805421778483, 45.003549975936025], [-74.64790231984267, 45.00348650222024], [-74.64768749471278, 45.00334179959561], [-74.6473451393104, 45.003304734188134], [-74.64730756271592, 45.00322361879394], [-74.64730810762454, 45.00313359288437], [-74.64724534800483, 45.003025385723916], [-74.64710625563777, 45.0029439241565], [-74.64705651688965, 45.0027817408222], [-74.6469048499502, 45.00268225188923], [-74.64676544053256, 45.00265480184333], [-74.64662619832838, 45.002600373326324], [-74.6461700618989, 45.00249993553716], [-74.6459290273045, 45.00249018356908], [-74.64553613613829, 45.00241696034792], [-74.64535888635737, 45.00235339291242], [-74.64519406878537, 45.002334861905716], [-74.64483756645816, 45.00253180720729], [-74.64443075652751, 45.00265656121266], [-74.64426460710263, 45.00285409363819], [-74.64385838607345, 45.002879832547876], [-74.64366756055948, 45.00296026309571], [-74.643450320864, 45.00321164340842], [-74.64239420629028, 45.00368544050712], [-74.64200002953083, 45.00381923191068], [-74.64179718811972, 45.003791580283824], [-74.6417213376827, 45.00374632463448], [-74.6413311136856, 45.00324099945285], [-74.64130671272912, 45.00308789050781], [-74.64104243315543, 45.002735978257824], [-74.64084166356258, 45.00237528018836], [-74.64080434092688, 45.00225812434654], [-74.64080654542065, 45.00190706499489], [-74.64107417759577, 45.00171887979189], [-74.64125285816597, 45.00154839336718]]]"
  }
}
````

## Harmonization

The harmonization of the data will be done with the following mapping:

#### Classes=>

| Ontology classes | URI format                                      | Transformation actions |
|------------------|-------------------------------------------------|------------------------|
| gn:parentADM4    | namespace#RTA-&lt;CFSAUID&gt;                   |                        |
| geosp:Geometry   | namespace#RTAPolygon-&lt;properties.CFSAUID&gt; |                        |

#### Object Properties=>

| Origin class    | Destination class | Relation          |
|-----------------|-------------------|-------------------|
| s4bldg:Building | geosp:Geometry    | geosp:hasGeometry |

#### Data properties=>

| Ontology classes | Origin field         | Harmonised field |
|------------------|----------------------|------------------|
| geosp:Geometry   | geometry.coordinates | geosp:asGeoJSON  |
| gn:parentADM4    | PRNAME               | gn:officialName  |


