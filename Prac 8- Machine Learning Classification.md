/**** Start of imports. If edited, may not auto-convert in the playground. ****/
var albury = 
    /* color: #ffc82d */
    /* shown: false */
    ee.Geometry.Point([146.98867400864796, -36.03720220333976]),
    s2data = ee.ImageCollection("COPERNICUS/S2_SR"),
    LT8data = ee.ImageCollection("LANDSAT/LC08/C01/T1_SR"),
    water = 
    /* color: #1829ff */
    /* shown: false */
    ee.FeatureCollection(
        [ee.Feature(
            ee.Geometry.Point([147.08529740237358, -36.206145729946755]),
            {
              "coverclass": 0,
              "system:index": "0"
            }),
        ee.Feature(
            ee.Geometry.Point([147.05439835452202, -36.17012405443928]),
            {
              "coverclass": 0,
              "system:index": "1"
            }),
        ee.Feature(
            ee.Geometry.Point([147.0914772119439, -36.01198741256012]),
            {
              "coverclass": 0,
              "system:index": "2"
            }),
        ee.Feature(
            ee.Geometry.Point([147.0420387353814, -36.139076712430814]),
            {
              "coverclass": 0,
              "system:index": "3"
            }),
        ee.Feature(
            ee.Geometry.Point([147.08873062991265, -36.04586095968257]),
            {
              "coverclass": 0,
              "system:index": "4"
            }),
        ee.Feature(
            ee.Geometry.Point([146.04948670574117, -35.99111106094229]),
            {
              "coverclass": 0,
              "system:index": "5"
            }),
        ee.Feature(
            ee.Geometry.Point([146.20010174664662, -35.29964279837522]),
            {
              "coverclass": 0,
              "system:index": "6"
            }),
        ee.Feature(
            ee.Geometry.Point([146.3987296985451, -36.006608900273854]),
            {
              "coverclass": 0,
              "system:index": "7"
            }),
        ee.Feature(
            ee.Geometry.Point([146.38907214802026, -36.05549686145651]),
            {
              "coverclass": 0,
              "system:index": "8"
            }),
        ee.Feature(
            ee.Geometry.Point([146.58540334730466, -35.98257817892644]),
            {
              "coverclass": 0,
              "system:index": "9"
            }),
        ee.Feature(
            ee.Geometry.Point([146.57081261461713, -36.06897567124541]),
            {
              "coverclass": 0,
              "system:index": "10"
            }),
        ee.Feature(
            ee.Geometry.Point([147.01935464010475, -35.99451272783153]),
            {
              "coverclass": 0,
              "system:index": "11"
            }),
        ee.Feature(
            ee.Geometry.Point([146.97204047308205, -36.07981237674931]),
            {
              "coverclass": 0,
              "system:index": "12"
            }),
        ee.Feature(
            ee.Geometry.Point([145.91008447618196, -35.95749684441811]),
            {
              "coverclass": 0,
              "system:index": "13"
            }),
        ee.Feature(
            ee.Geometry.Point([145.89322344584744, -35.952969646213]),
            {
              "coverclass": 0,
              "system:index": "14"
            }),
        ee.Feature(
            ee.Geometry.Point([145.90657099424067, -35.924646635904594]),
            {
              "coverclass": 0,
              "system:index": "15"
            }),
        ee.Feature(
            ee.Geometry.Point([146.85014831029696, -36.100238947681646]),
            {
              "coverclass": 0,
              "system:index": "16"
            }),
        ee.Feature(
            ee.Geometry.Point([146.88225971662325, -36.07989341310985]),
            {
              "coverclass": 0,
              "system:index": "17"
            }),
        ee.Feature(
            ee.Geometry.Point([146.879513134592, -36.07677178797705]),
            {
              "coverclass": 0,
              "system:index": "18"
            }),
        ee.Feature(
            ee.Geometry.Point([146.21355998779381, -36.0510655164112]),
            {
              "coverclass": 0,
              "system:index": "19"
            }),
        ee.Feature(
            ee.Geometry.Point([147.09707481012111, -35.29462661274142]),
            {
              "coverclass": 0,
              "system:index": "20"
            }),
        ee.Feature(
            ee.Geometry.Point([146.07580613914573, -36.0160202027248]),
            {
              "coverclass": 0,
              "system:index": "21"
            }),
        ee.Feature(
            ee.Geometry.Point([146.1687502667623, -36.02774931693572]),
            {
              "coverclass": 0,
              "system:index": "22"
            }),
        ee.Feature(
            ee.Geometry.Point([146.1776498362737, -36.026643022847054]),
            {
              "coverclass": 0,
              "system:index": "23"
            }),
        ee.Feature(
            ee.Geometry.Point([146.50924624827866, -36.006605140876026]),
            {
              "coverclass": 0,
              "system:index": "24"
            }),
        ee.Feature(
            ee.Geometry.Point([146.2495429856281, -36.20974857092253]),
            {
              "coverclass": 0,
              "system:index": "25"
            }),
        ee.Feature(
            ee.Geometry.Point([147.00583377309255, -35.94265702300456]),
            {
              "coverclass": 0,
              "system:index": "26"
            }),
        ee.Feature(
            ee.Geometry.Point([146.95973893867654, -36.15279584361514]),
            {
              "coverclass": 0,
              "system:index": "27"
            }),
        ee.Feature(
            ee.Geometry.Point([146.738718832345, -36.02534156012704]),
            {
              "coverclass": 0,
              "system:index": "28"
            }),
        ee.Feature(
            ee.Geometry.Point([146.3480032671665, -35.92044208175156]),
            {
              "coverclass": 0,
              "system:index": "29"
            })]),
    fields = 
    /* color: #bf04c2 */
    /* shown: false */
    ee.FeatureCollection(
        [ee.Feature(
            ee.Geometry.Point([146.12421522945843, -36.07656294951116]),
            {
              "coverclass": 1,
              "system:index": "0"
            }),
        ee.Feature(
            ee.Geometry.Point([146.27536307186566, -36.10340494680888]),
            {
              "coverclass": 1,
              "system:index": "1"
            }),
        ee.Feature(
            ee.Geometry.Point([146.5643657638505, -36.02433465289266]),
            {
              "coverclass": 1,
              "system:index": "2"
            }),
        ee.Feature(
            ee.Geometry.Point([146.1087935420894, -35.586304645308275]),
            {
              "coverclass": 1,
              "system:index": "3"
            }),
        ee.Feature(
            ee.Geometry.Point([146.69596128195755, -35.32111243686284]),
            {
              "coverclass": 1,
              "system:index": "4"
            }),
        ee.Feature(
            ee.Geometry.Point([146.52596623600868, -35.66847424137173]),
            {
              "coverclass": 1,
              "system:index": "5"
            }),
        ee.Feature(
            ee.Geometry.Point([146.08074099892818, -35.80488810241078]),
            {
              "coverclass": 1,
              "system:index": "6"
            }),
        ee.Feature(
            ee.Geometry.Point([146.8251857663918, -35.804149272708074]),
            {
              "coverclass": 1,
              "system:index": "7"
            }),
        ee.Feature(
            ee.Geometry.Point([145.92595248308783, -36.17302269098805]),
            {
              "coverclass": 1,
              "system:index": "8"
            }),
        ee.Feature(
            ee.Geometry.Point([146.58102098831256, -35.46596797506324]),
            {
              "coverclass": 1,
              "system:index": "9"
            }),
        ee.Feature(
            ee.Geometry.Point([146.80468647810574, -35.79466628399962]),
            {
              "coverclass": 1,
              "system:index": "10"
            }),
        ee.Feature(
            ee.Geometry.Point([146.60186856123562, -35.819725113179295]),
            {
              "coverclass": 1,
              "system:index": "11"
            }),
        ee.Feature(
            ee.Geometry.Point([146.15965051383913, -35.78437670275432]),
            {
              "coverclass": 1,
              "system:index": "12"
            }),
        ee.Feature(
            ee.Geometry.Point([146.31020745893957, -35.73810324747948]),
            {
              "coverclass": 1,
              "system:index": "13"
            }),
        ee.Feature(
            ee.Geometry.Point([147.05752481463938, -35.584576181723556]),
            {
              "coverclass": 1,
              "system:index": "14"
            }),
        ee.Feature(
            ee.Geometry.Point([146.86243165973215, -35.60544439286159]),
            {
              "coverclass": 1,
              "system:index": "15"
            }),
        ee.Feature(
            ee.Geometry.Point([146.39725309785743, -36.195818054362206]),
            {
              "coverclass": 1,
              "system:index": "16"
            }),
        ee.Feature(
            ee.Geometry.Point([146.41115766939063, -36.179331092176184]),
            {
              "coverclass": 1,
              "system:index": "17"
            }),
        ee.Feature(
            ee.Geometry.Point([146.07933717285687, -36.145340106575915]),
            {
              "coverclass": 1,
              "system:index": "18"
            }),
        ee.Feature(
            ee.Geometry.Point([145.90569666472635, -35.53922573734105]),
            {
              "coverclass": 1,
              "system:index": "19"
            }),
        ee.Feature(
            ee.Geometry.Point([146.47451636796617, -35.607685692627115]),
            {
              "coverclass": 1,
              "system:index": "20"
            }),
        ee.Feature(
            ee.Geometry.Point([146.03990119911907, -35.34295701628923]),
            {
              "coverclass": 1,
              "system:index": "21"
            }),
        ee.Feature(
            ee.Geometry.Point([147.01561454095634, -35.32421006437286]),
            {
              "coverclass": 1,
              "system:index": "22"
            }),
        ee.Feature(
            ee.Geometry.Point([146.76271472793127, -35.37762796485154]),
            {
              "coverclass": 1,
              "system:index": "23"
            }),
        ee.Feature(
            ee.Geometry.Point([146.2758235547906, -36.16024985786701]),
            {
              "coverclass": 1,
              "system:index": "24"
            }),
        ee.Feature(
            ee.Geometry.Point([146.2772344818018, -36.22456580327833]),
            {
              "coverclass": 1,
              "system:index": "25"
            }),
        ee.Feature(
            ee.Geometry.Point([146.04591413421605, -36.18155748412024]),
            {
              "coverclass": 1,
              "system:index": "26"
            }),
        ee.Feature(
            ee.Geometry.Point([146.5544310805636, -36.07062212337269]),
            {
              "coverclass": 1,
              "system:index": "27"
            }),
        ee.Feature(
            ee.Geometry.Point([146.56941553196475, -35.93009429161199]),
            {
              "coverclass": 1,
              "system:index": "28"
            }),
        ee.Feature(
            ee.Geometry.Point([146.27796235603788, -35.85600063897127]),
            {
              "coverclass": 1,
              "system:index": "29"
            })]),
    forest = 
    /* color: #89ff2f */
    /* shown: false */
    ee.FeatureCollection(
        [ee.Feature(
            ee.Geometry.Point([146.15005693708756, -36.22331812880466]),
            {
              "coverclass": 2,
              "system:index": "0"
            }),
        ee.Feature(
            ee.Geometry.Point([146.20498857771256, -36.20974565223111]),
            {
              "coverclass": 2,
              "system:index": "1"
            }),
        ee.Feature(
            ee.Geometry.Point([146.5689684273509, -36.21529427424146]),
            {
              "coverclass": 2,
              "system:index": "2"
            }),
        ee.Feature(
            ee.Geometry.Point([146.69599784629622, -36.22415757056499]),
            {
              "coverclass": 2,
              "system:index": "3"
            }),
        ee.Feature(
            ee.Geometry.Point([146.65239585655013, -36.16015311475426]),
            {
              "coverclass": 2,
              "system:index": "4"
            }),
        ee.Feature(
            ee.Geometry.Point([146.57755149619857, -36.12993371576594]),
            {
              "coverclass": 2,
              "system:index": "5"
            }),
        ee.Feature(
            ee.Geometry.Point([146.7498896206264, -36.0997532172781]),
            {
              "coverclass": 2,
              "system:index": "6"
            }),
        ee.Feature(
            ee.Geometry.Point([147.06774411177787, -35.79357103232308]),
            {
              "coverclass": 2,
              "system:index": "7"
            }),
        ee.Feature(
            ee.Geometry.Point([146.89605684544253, -35.668745157227114]),
            {
              "coverclass": 2,
              "system:index": "8"
            }),
        ee.Feature(
            ee.Geometry.Point([146.45155809266478, -35.53930654297502]),
            {
              "coverclass": 2,
              "system:index": "9"
            }),
        ee.Feature(
            ee.Geometry.Point([146.48232839448363, -35.545906329638136]),
            {
              "coverclass": 2,
              "system:index": "10"
            }),
        ee.Feature(
            ee.Geometry.Point([146.15246692633514, -35.49805876560669]),
            {
              "coverclass": 2,
              "system:index": "11"
            }),
        ee.Feature(
            ee.Geometry.Point([145.99347003169447, -35.459985764395704]),
            {
              "coverclass": 2,
              "system:index": "12"
            }),
        ee.Feature(
            ee.Geometry.Point([146.00462802119642, -35.45816806079412]),
            {
              "coverclass": 2,
              "system:index": "13"
            }),
        ee.Feature(
            ee.Geometry.Point([147.07193127041697, -35.277734564404554]),
            {
              "coverclass": 2,
              "system:index": "14"
            }),
        ee.Feature(
            ee.Geometry.Point([147.0996545827949, -35.290976507486064]),
            {
              "coverclass": 2,
              "system:index": "15"
            }),
        ee.Feature(
            ee.Geometry.Point([146.93056894907994, -35.30173288592649]),
            {
              "coverclass": 2,
              "system:index": "16"
            }),
        ee.Feature(
            ee.Geometry.Point([145.96406603283353, -35.25877448244363]),
            {
              "coverclass": 2,
              "system:index": "17"
            }),
        ee.Feature(
            ee.Geometry.Point([145.89497875348619, -35.955946498743806]),
            {
              "coverclass": 2,
              "system:index": "18"
            }),
        ee.Feature(
            ee.Geometry.Point([145.89153605754424, -35.966648336665635]),
            {
              "coverclass": 2,
              "system:index": "19"
            }),
        ee.Feature(
            ee.Geometry.Point([146.40223744701584, -35.74644266743307]),
            {
              "coverclass": 2,
              "system:index": "20"
            }),
        ee.Feature(
            ee.Geometry.Point([146.59775081932295, -35.7217884310733]),
            {
              "coverclass": 2,
              "system:index": "21"
            }),
        ee.Feature(
            ee.Geometry.Point([146.90032367691532, -35.72838769870337]),
            {
              "coverclass": 2,
              "system:index": "22"
            }),
        ee.Feature(
            ee.Geometry.Point([146.36208278391098, -35.39769816341966]),
            {
              "coverclass": 2,
              "system:index": "23"
            }),
        ee.Feature(
            ee.Geometry.Point([146.64369871492514, -35.248901454785404]),
            {
              "coverclass": 2,
              "system:index": "24"
            }),
        ee.Feature(
            ee.Geometry.Point([146.40146081263222, -35.898054353444124]),
            {
              "coverclass": 2,
              "system:index": "25"
            }),
        ee.Feature(
            ee.Geometry.Point([146.18316636261565, -36.057540904569066]),
            {
              "coverclass": 2,
              "system:index": "26"
            }),
        ee.Feature(
            ee.Geometry.Point([146.14797578034026, -36.037901711673804]),
            {
              "coverclass": 2,
              "system:index": "27"
            }),
        ee.Feature(
            ee.Geometry.Point([146.1593483465634, -36.04362742403009]),
            {
              "coverclass": 2,
              "system:index": "28"
            }),
        ee.Feature(
            ee.Geometry.Point([146.25353002840703, -36.01050351156487]),
            {
              "coverclass": 2,
              "system:index": "29"
            })]),
    urban = 
    /* color: #3dffe4 */
    /* shown: false */
    ee.FeatureCollection(
        [ee.Feature(
            ee.Geometry.Point([146.8905324740765, -36.11968052987402]),
            {
              "coverclass": 3,
              "system:index": "0"
            }),
        ee.Feature(
            ee.Geometry.Point([146.88980346713788, -36.120669071685676]),
            {
              "coverclass": 3,
              "system:index": "1"
            }),
        ee.Feature(
            ee.Geometry.Point([146.9135442824359, -36.08175625333696]),
            {
              "coverclass": 3,
              "system:index": "2"
            }),
        ee.Feature(
            ee.Geometry.Point([146.9432417006488, -36.06621663842794]),
            {
              "coverclass": 3,
              "system:index": "3"
            }),
        ee.Feature(
            ee.Geometry.Point([146.9642167217494, -36.03369170371284]),
            {
              "coverclass": 3,
              "system:index": "4"
            }),
        ee.Feature(
            ee.Geometry.Point([146.96651269266616, -36.039920897829376]),
            {
              "coverclass": 3,
              "system:index": "5"
            }),
        ee.Feature(
            ee.Geometry.Point([146.93286527426582, -36.150489932931436]),
            {
              "coverclass": 3,
              "system:index": "6"
            }),
        ee.Feature(
            ee.Geometry.Point([146.9457398775373, -36.145846311087475]),
            {
              "coverclass": 3,
              "system:index": "7"
            }),
        ee.Feature(
            ee.Geometry.Point([146.94897552977997, -36.16102369742535]),
            {
              "coverclass": 3,
              "system:index": "8"
            }),
        ee.Feature(
            ee.Geometry.Point([146.93149133134224, -36.1748333315971]),
            {
              "coverclass": 3,
              "system:index": "9"
            }),
        ee.Feature(
            ee.Geometry.Point([146.00398489705074, -36.01151065947871]),
            {
              "coverclass": 3,
              "system:index": "10"
            }),
        ee.Feature(
            ee.Geometry.Point([146.01834007969845, -36.01192722847119]),
            {
              "coverclass": 3,
              "system:index": "11"
            }),
        ee.Feature(
            ee.Geometry.Point([145.99929072767105, -36.028290929878835]),
            {
              "coverclass": 3,
              "system:index": "12"
            }),
        ee.Feature(
            ee.Geometry.Point([146.00619358184716, -35.97458599927259]),
            {
              "coverclass": 3,
              "system:index": "13"
            }),
        ee.Feature(
            ee.Geometry.Point([145.98701196377297, -35.98613062736962]),
            {
              "coverclass": 3,
              "system:index": "14"
            }),
        ee.Feature(
            ee.Geometry.Point([146.86054942342042, -36.10654582842481]),
            {
              "coverclass": 3,
              "system:index": "15"
            }),
        ee.Feature(
            ee.Geometry.Point([146.9864693439247, -35.99530234079321]),
            {
              "coverclass": 3,
              "system:index": "16"
            }),
        ee.Feature(
            ee.Geometry.Point([146.89717881749885, -35.97110985335516]),
            {
              "coverclass": 3,
              "system:index": "17"
            }),
        ee.Feature(
            ee.Geometry.Point([146.36793879290428, -35.98681362381208]),
            {
              "coverclass": 3,
              "system:index": "18"
            }),
        ee.Feature(
            ee.Geometry.Point([146.4602407054912, -36.05394463091408]),
            {
              "coverclass": 3,
              "system:index": "19"
            }),
        ee.Feature(
            ee.Geometry.Point([146.46212990661388, -36.05556861708722]),
            {
              "coverclass": 3,
              "system:index": "20"
            }),
        ee.Feature(
            ee.Geometry.Point([146.71887815335558, -36.07594357638318]),
            {
              "coverclass": 3,
              "system:index": "21"
            }),
        ee.Feature(
            ee.Geometry.Point([147.03653031221572, -35.667448431745875]),
            {
              "coverclass": 3,
              "system:index": "22"
            }),
        ee.Feature(
            ee.Geometry.Point([147.03891055684696, -35.52570761853577]),
            {
              "coverclass": 3,
              "system:index": "23"
            }),
        ee.Feature(
            ee.Geometry.Point([147.03383599143677, -35.51730836900401]),
            {
              "coverclass": 3,
              "system:index": "24"
            }),
        ee.Feature(
            ee.Geometry.Point([146.9354633737206, -36.04831900714366]),
            {
              "coverclass": 3,
              "system:index": "25"
            }),
        ee.Feature(
            ee.Geometry.Point([146.94907912756275, -36.06066832363694]),
            {
              "coverclass": 3,
              "system:index": "26"
            }),
        ee.Feature(
            ee.Geometry.Point([146.94972285772633, -36.055125999424654]),
            {
              "coverclass": 3,
              "system:index": "27"
            }),
        ee.Feature(
            ee.Geometry.Point([146.95932499421963, -36.06937569162954]),
            {
              "coverclass": 3,
              "system:index": "28"
            }),
        ee.Feature(
            ee.Geometry.Point([147.00063010255505, -36.1331529074522]),
            {
              "coverclass": 3,
              "system:index": "29"
            })]),
    baresoil = 
    /* color: #fdff66 */
    /* shown: false */
    ee.FeatureCollection(
        [ee.Feature(
            ee.Geometry.Point([147.0141537945872, -36.06748590328849]),
            {
              "coverclass": 4,
              "system:index": "0"
            }),
        ee.Feature(
            ee.Geometry.Point([147.0548684524325, -36.04076783390867]),
            {
              "coverclass": 4,
              "system:index": "1"
            }),
        ee.Feature(
            ee.Geometry.Point([147.06529785127515, -35.97549787970588]),
            {
              "coverclass": 4,
              "system:index": "2"
            }),
        ee.Feature(
            ee.Geometry.Point([147.0483033749568, -35.96167411875103]),
            {
              "coverclass": 4,
              "system:index": "3"
            }),
        ee.Feature(
            ee.Geometry.Point([146.69673931560544, -35.49755121115982]),
            {
              "coverclass": 4,
              "system:index": "4"
            }),
        ee.Feature(
            ee.Geometry.Point([145.92228770750268, -35.32092182032833]),
            {
              "coverclass": 4,
              "system:index": "5"
            }),
        ee.Feature(
            ee.Geometry.Point([145.9071815063308, -35.2895416063955]),
            {
              "coverclass": 4,
              "system:index": "6"
            }),
        ee.Feature(
            ee.Geometry.Point([146.07043147581322, -35.249598297677245]),
            {
              "coverclass": 4,
              "system:index": "7"
            }),
        ee.Feature(
            ee.Geometry.Point([146.0700852416068, -35.27116562178178]),
            {
              "coverclass": 4,
              "system:index": "8"
            }),
        ee.Feature(
            ee.Geometry.Point([146.05655540348735, -35.34529267357549]),
            {
              "coverclass": 4,
              "system:index": "9"
            }),
        ee.Feature(
            ee.Geometry.Point([146.1026893985435, -35.31808904649832]),
            {
              "coverclass": 4,
              "system:index": "10"
            }),
        ee.Feature(
            ee.Geometry.Point([146.12040987789797, -35.277332916886095]),
            {
              "coverclass": 4,
              "system:index": "11"
            }),
        ee.Feature(
            ee.Geometry.Point([146.33231083301783, -35.304479159989704]),
            {
              "coverclass": 4,
              "system:index": "12"
            }),
        ee.Feature(
            ee.Geometry.Point([147.0307502251764, -35.24830260702401]),
            {
              "coverclass": 4,
              "system:index": "13"
            }),
        ee.Feature(
            ee.Geometry.Point([146.07951872224942, -35.508591463609186]),
            {
              "coverclass": 4,
              "system:index": "14"
            }),
        ee.Feature(
            ee.Geometry.Point([146.3242989210384, -35.74156992856357]),
            {
              "coverclass": 4,
              "system:index": "15"
            }),
        ee.Feature(
            ee.Geometry.Point([146.1253421420241, -35.76217120233139]),
            {
              "coverclass": 4,
              "system:index": "16"
            }),
        ee.Feature(
            ee.Geometry.Point([146.06355571337076, -35.70627455497017]),
            {
              "coverclass": 4,
              "system:index": "17"
            }),
        ee.Feature(
            ee.Geometry.Point([146.02256450726875, -35.70787259126877]),
            {
              "coverclass": 4,
              "system:index": "18"
            }),
        ee.Feature(
            ee.Geometry.Point([145.95750004032342, -36.21439116448468]),
            {
              "coverclass": 4,
              "system:index": "19"
            }),
        ee.Feature(
            ee.Geometry.Point([145.93596160285972, -36.15973155103574]),
            {
              "coverclass": 4,
              "system:index": "20"
            }),
        ee.Feature(
            ee.Geometry.Point([146.243501338075, -35.42185238737785]),
            {
              "coverclass": 4,
              "system:index": "21"
            }),
        ee.Feature(
            ee.Geometry.Point([146.26993719012577, -35.41588943970618]),
            {
              "coverclass": 4,
              "system:index": "22"
            }),
        ee.Feature(
            ee.Geometry.Point([146.389695121771, -35.37987933174795]),
            {
              "coverclass": 4,
              "system:index": "23"
            }),
        ee.Feature(
            ee.Geometry.Point([146.53766781416675, -35.46124089682024]),
            {
              "coverclass": 4,
              "system:index": "24"
            }),
        ee.Feature(
            ee.Geometry.Point([146.9249250381007, -35.391570813248585]),
            {
              "coverclass": 4,
              "system:index": "25"
            }),
        ee.Feature(
            ee.Geometry.Point([147.07546401717684, -35.39886848781668]),
            {
              "coverclass": 4,
              "system:index": "26"
            }),
        ee.Feature(
            ee.Geometry.Point([146.49770584695833, -35.30383831099436]),
            {
              "coverclass": 4,
              "system:index": "27"
            }),
        ee.Feature(
            ee.Geometry.Point([146.25899873673083, -35.25138233569762]),
            {
              "coverclass": 4,
              "system:index": "28"
            }),
        ee.Feature(
            ee.Geometry.Point([145.96786914340436, -35.38552555403888]),
            {
              "coverclass": 4,
              "system:index": "29"
            })]);
/***** End of imports. If edited, may not auto-convert in the playground. *****/
/* ACKNOWLEDGEMENT
Google Earth Engine Developers
Google Earth Engine Team
*/
/*
Please be sure you attempt this practical using the practical manual. The practical manual gives thorough explanations
to the concepts and scripts. Using the practical manual, the commands, arguments, or parameters used in the scripts will
make more sense to you. Also, you will test your understanding of the remote sensing principles as you work through challenge tasks
and revision questions.
*/
////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
/*Prac 8: Supervised classification techniques
In this prac, we will explore a range of supervised classification techniques to discriminate
between different surface types, inlcuding water, pasture fields, forest, urban, and bare soil.
Further, we will qualitatively and quantitively assess the performances of the classifiers
Thus, at the end of this prac you should be able to:
1, create a feature collection from feature classes to train/test classifiers
2, export training data to GEE Asset and Google Drive
3, classify an image using supervised classification techniques
4, evaluate the accuracy of a classifier 
*/
 
 ///////////////////////////////////////////////////////////////////////////////////////////////////////////////////
 ////1, Supervised classification- minimum distance classifier
 
 // Given the import function brings all of the images we would need to filter this collection
// we can filter using study area, data and cloud cover requirement

//let's define this range of data sets into a variable 
    var sen2_image = ee.Image(s2data  // filterDate: limit this collection to a particular date

    // filterDate: limit this collection to a particular date
    .filterDate("2018-01-01", "2019-12-31")

    // Further filter image to study area
    .filterBounds(albury)

    // sort data by cloud cover, from highest quality to lowest.
    .sort("CLOUD_COVERAGE_ASSESSMENT")

    // Select the first image as conisdered to be the most cloud free
    .first());

// finally, print the image to the console.
    print("A Sentinel-2 scene containing Albury, NSW:", sen2_image); // The image was acquired on the 27 February 2019 with a cloud coverage assessment of 0.007% 

// Display the image as true colour and false colour composites

// first set up the visualisation parameters
var tcc={bands:["B4","B3","B2"], min:0, max:6000}; // true colour composite
var fcc={bands:["B8","B4","B3"], min: 0, max:6000}; //standrad false colour composite

//Add true and false colour images to base map
Map.addLayer(sen2_image, tcc, 'True colour display');
Map.addLayer(sen2_image, fcc, 'Standard false colour display');

//Onscreen collection of training data points for surface types (this is covered in Prac 6)

/*
Merge the five classes into a single collection for training data collection
*/

// merge five geometries into a single collection
var surfaceTypes = water.merge(fields).merge(forest).merge(urban).merge(baresoil);

//print feature collection 
print(surfaceTypes);

// export 'surfaceTypes' (i.e.,feature collections merged into one collection) to GEE Assets. 
// You can export to your Google Drive too. Both codes are provided but the prac run the export to Assest

// export to GEE Assets
Export.table.toAsset({
  collection: surfaceTypes,
  description: 'trainingDataForSPA217',
  assetId: 'trainingDataForSPA217'
}); // be sure to go to 'Tasks' and run this to finish exporting to 'Assets'. 
//Refresh 'Assets' to finally see the data. It is under 'CLOUD ASSETS'

// export training (i.e., 'surfaceTypes) to your Google Drive. Remove the two forward slashes to run code (optional)
Export.table.toDrive({
  collection: surfaceTypes,
  description: 'trainingDataForSPA217',
  fileFormat: 'SHP'
});

/* Now let's use this feature collection to collect training data (specral reflectance for each point data)
You have to overlay these training point features on the image to extract the spectra
By doing this, the spectral bands for each point will be added as new properties to your feature collection.
*/
// use these bands as the features
var bands = ['B2', 'B3', 'B4', 'B8']; // selected these bands because they all have a spatial resolution of 10m

// increase the number of features by adding the 20 m bands too. We'll upsample the 10m bands
var bands_2 = ['B2', 'B3', 'B4', 'B5','B6', 'B7','B8', 'B8A','B11','B12'];

// overlay the points showing surface types on the imagery to get training
var training = sen2_image.select(bands).sampleRegions({
  collection: surfaceTypes,
  properties: ['coverclass'],
  scale: 10
}); 

// print the training data
print(training, 'training');

// Train a minimum distance classifier 
var minimum_distance = ee.Classifier.minimumDistance().train({
  features: training,
  classProperty: 'coverclass',
  inputProperties: bands
});

//Run the classification
var miniDis_classifier = sen2_image.select(bands).classify(minimum_distance);

//visualise the performance of minimum distanace classifier... 
//... blue =water; lightgreen=cropping fields; darkgreen=forest; brown=baresoil; white=urban
Map.centerObject(surfaceTypes, 10);
Map.addLayer(miniDis_classifier,
{min: 0, max: 4, palette: ['blue','lightgreen', 'darkgreen','white','brown']},
'minimum distance classification');

/*
In the following supervised machine learning classifiers, we will add the 20 bands too as features.
This means that we will upsample the 10 m bands to 20m. We update the existing training variable 
to account for this change.
*/

// update the training set- overlay the points showing surface types on the imagery to get training
var training = sen2_image.select(bands_2).sampleRegions({
  collection: surfaceTypes,
  properties: ['coverclass'],
  scale: 20 //changed from 10. The number of features also changed from 4 to 10.
});

////2, Supervised classification- Classification and Regression Trees (CART)

// Train a CART classifier with default parameters
var cart = ee.Classifier.smileCart().train({
  features: training,
  classProperty: 'coverclass',
  inputProperties: bands_2
});

// Classify the image with the same bands used for training.
var cart_classifier = sen2_image.select(bands_2).classify(cart);

// visualise the results.
Map.addLayer(cart_classifier,
             {min: 0, max: 4, palette: ['blue','lightgreen', 'darkgreen','white','brown']},
             'CART');


////3, Supervised classification- Random Forest 

// Make a Random Forest classifier and train it.
var rf = ee.Classifier.smileRandomForest(10)
    .train({
      features: training,
      classProperty: 'coverclass',
      inputProperties: bands_2
    });

// apply random forest classifier to the original image 
var rf_classifier = sen2_image.classify(rf);

// visualise random forest classification results 
Map.addLayer(rf_classifier,
             {min: 0, max: 4, palette: ['blue','lightgreen', 'darkgreen','white','brown']},
             'random forest');





