<template>
  <div>
    <Picture :pictures="pictures" v-show="randomPic" />
    <OnePicture :pictures="pictures" v-show="choiceOnePic"/>
    <div v-show="displayText">
      <div class="divChoose">
        <h2>Choix du test</h2>
        <p>
          Affichage de toutes les images disponibles, vues au programme.
          Possibilité d'avoir l'exercice au choix. Vous aurez votre score à chaque
          fin d'image. Les mots ont leur importance, faites-y attention.
        </p>
        <div class="box-3">
          <div class="btn btn-three" @click="showOnePic">
            <span>COMMENCER</span>
          </div>
        </div>
      </div>
      <div class="divRandom">
        <h2>Test complet</h2>
        <p>
          Examen complet, comportant toutes les images du programme. Celles-ci
          sont affichées aléatoirement. Vous aurez votre score à chaque fin
          d'image. Les mots ont leur importance, faites-y attention.
        </p>
        <div class="box-3">
          <div class="btn btn-three" @click="showRandomPic">
            <span >COMMENCER</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Picture from "@/components/Picture.vue";
import OnePicture from "@/components/OnePicture.vue";


export default {
  name: "exercise",
  components: {
    Picture,
    OnePicture
  },

  data() {
    return {
      pictures: [
        {
          id: 0,
          name: "Squelette",
          nbCorrection: 2,
          answers: [
            {
              number: 1,
              correctAnswer: ["crâne", "Crâne", "crane", "Crane"]
            },
            {
              number: 2,
              correctAnswer: ["face", "Face"]
            },
            {
              number: 3,
              correctAnswer: ["vertèbres", "Vertèbres", "vertebres", "Vertebres", "vertébres", "Vertébres", "vertébre", "vertebre", "Vertebre", "vertèbre", "Vertèbre", "Vertébre"]
            },
            {
              number: 4,
              correctAnswer: ["clavicule", "Clavicule", "clavicul", "Clavicul"]
            },
            {
              number: 5,
              correctAnswer: ["scapula", "Scapula"]
            },
            {
              number: 6,
              correctAnswer: ["humérus", "Humérus"]
            },
            {
              number: 7,
              correctAnswer: ["vertèbres", "Vertèbres", "vertebres", "Vertebres", "vertébres", "Vertébres", "vertébre", "vertebre", "Vertebre", "vertèbre", "Vertèbre", "Vertébre"]
            },
            {
              number: 8,
              correctAnswer: ["radius", "Radius"]
            },
            {
              number: 9,
              correctAnswer: ["ulna", "Ulna"] 
            },
            {
              number: 10,
              correctAnswer: ["carpe", "Carpe"]
            },
            {
              number: 11,
              correctAnswer: ["métacarpe", "Métacarpe", "metacarpe", "Metacarpe"]
            },
            {
              number: 12,
              correctAnswer: ["phalanges de la main", "Phalanges de la main", "phalange de la main", "Phalange de la main", "phalange des mains", "Phalange des mains", "phalanges des mains", "Phalanges des mains", "phalange","Phalange", "phalanges","Phalanges"]
            },
            {
              number: 13,
              correctAnswer: ["sternum", "Sternum"]
            },
            {
              number: 14,
              correctAnswer: ["côte", "Côte", "côtes", "Côtes"]
            },
            {
              number: 15,
              correctAnswer: ["cartillage costal", "Cartillage costal"]
            },
            {
              number: 16,
              correctAnswer: ["os coxal", "Os coxal"]
            },
            {
              number: 17,
              correctAnswer: ["sacrum", "Sacrum"]
            },
            {
              number: 18,
              correctAnswer: ["fémur", "Fémur", "femur", "Femur"]
            },
            {
              number: 19,
              correctAnswer: ["patella", "Patella"]
            },
            {
              number: 20,
              correctAnswer: ["tibia", "Tibia"]
            },
            {
              number: 21,
              correctAnswer: ["fibula", "Fibula"]
            },
            {
              number: 22,
              correctAnswer: ["tarse", "Tarse"]
            },
            {
              number: 23,
              correctAnswer: ["métatarse", "Métatarse", "metatarse", "Metatarse"]
            },
            {
              number: 24,
              correctAnswer: ["phalanges des orteils", "Phalanges des orteils", "phalange des orteils", "Phalange des orteils","phalanges de l'orteil", "Phalanges de l'orteil", "phalange de l'orteil", "Phalange de l'orteil"  ,"phalange","Phalange", "phalanges","Phalanges"]
            },
          ],
        },
        {
          id: 1,
          name: "Os long (humérus)",
          nbCorrection: 4,
          answers: [
            {
              number: 1,
              correctAnswer: ["os spongieux","Os spongieux"]
            },
            {
              number: 2,
              correctAnswer: ["cartillage articulaire","Cartillage articulaire"]
            },
            {
              number: 3,
              correctAnswer: ["ligne épiphysaire", "Ligne épiphysaire"]
            },
            {
              number: 4,
              correctAnswer: ["périoste", "Périoste"]
            },
            {
              number: 5,
              correctAnswer: ["os compact", "Os compact"]
            },
            {
              number: 6,
              correctAnswer: ["cavité médulaire", "Cavité médulaire"]
            },
            {
              number: 7,
              correctAnswer: ["épiphyse proximale", "Epiphyse proximale"]
            },
            {
              number: 8,
              correctAnswer: ["diaphyse", "Diaphyse"]
            },
            {
              number: 9,
              correctAnswer: ["épiphyse distale", "Epiphyse distale"]
            },
          ],
        },
        {
          id: 2,
          name: "Cœur",
          nbCorrection: 6,
          answers: [
            {
              number: 1,
              correctAnswer: ["veine cave supérieure", "Veine cave supérieure", "veine cave superieure", "Veine cave superieure"]
            },
            {
              number: 2,
              correctAnswer: ["veine pulmonaire", "Veine pulmonaire"]
            },
            {
              number: 3,
              correctAnswer: ["valve pulmonaire", "Valve pulmonaire"]
            },
            {
              number: 4,
              correctAnswer: ["oreillette droite", "Oreillette droite"]
            },
            {
              number: 5,
              correctAnswer: ["valve tricuspide", "Valve tricuspide"]
            },
            {
              number: 6,
              correctAnswer: ["ventricule droit", "Ventricule droit"]
            },
            {
              number: 7,
              correctAnswer: ["aorte", "Aorte"]
            },
            {
              number: 8,
              correctAnswer: ["artère pulmonaire", "Artère pulmonaire", "artere pulmonaire", "Artere pulmonaire"]
            },
            {
              number: 9,
              correctAnswer: ["oreillette gauche", "Oreillette gauche"]
            },
            {
              number: 10,
              correctAnswer: ["valve aortique", "Valve aortique"]
            },
            {
              number: 11,
              correctAnswer: ["valve mitrale", "Valve mitrale"]
            },
            {
              number: 12,
              correctAnswer: ["cordages", "Cordages" , "cordage", "Cordage"]
            },
            {
              number: 13,
              correctAnswer: ["ventricule gauche", "Ventricule gauche"]
            },
            {
              number: 14,
              correctAnswer: ["piliers", "Piliers", "pilier", "Pilier"]
            },
          ],
        },
        {
          id: 3,
          name: "Circulation sanguine simplifiée",
          nbCorrection: 8,
          answers: [
            {
              number: 1,
              correctAnswer: ["artère pulmonaire", "Artère pulmonaire", "artere pulmonaire", "Artere pulmonaire"]
            },
            {
              number: 2,
              correctAnswer: ["poumons", "Poumons", "poumon", "Poumon"]
            },
            {
              number: 3,
              correctAnswer: ["veine pulmonaire", "Veine pulmonaire"]
            },
            {
              number: 4,
              correctAnswer: ["aorte", "Aorte"]
            },
            {
              number: 5,
              correctAnswer: ["coeur", "Coeur" , "cœur", "Cœur"]
            },
            {
              number: 6,
              correctAnswer: ["veine cave", "Veine cave"]
            },
          ],
        },
        {
          id: 4,
          name: "Réticulum Endoplasmique et Ribosome",
          nbCorrection: 10,
          answers: [
            {
              number: 1,
              correctAnswer: ["pore nucléaire", "Pore nucléaire", "pore nucleaire", "Pore nucleaire"]
            },
            {
              number: 2,
              correctAnswer: ["noyau", "Noyau"]
            },
            {
              number: 3,
              correctAnswer: ["réticulum endoplasmique granuleux", "Réticulum endoplasmique granuleux", "reticulum endoplasmique granuleux", "Reticulum endoplasmique granuleux"]
            },
            {
              number: 4,
              correctAnswer: ["ribosome", "Ribosome"]
            },
            {
              number: 5,
              correctAnswer: ["réticulum", "Réticulum", "reticulum", "Reticulum"]
            },
            {
              number: 6,
              correctAnswer: ["vésicule", "Vésicule", "vesicule", "Vesicule"]
            },
            {
              number: 7,
              correctAnswer: ["protéine transportée", "Protéine transportée"]
            },
            {
              number: 8,
              correctAnswer: ["citerne de l'appareil de Golgi", "Citerne de l'appareil de Golgi"]
            },
            {
              number: 9,
              correctAnswer: ["appareil de Golgi", "Appareil de Golgi"]
            },
          ],
        },
        {
          id: 5,
          name: "Anatomie de l'aorte",
          nbCorrection: 12,
          answers: [
            {
              number: 1,
              correctAnswer: ["aorte ascendante", "Aorte ascendante"]
            },
            {
              number: 2,
              correctAnswer: ["crosse aortique", "Crosse aortique"]
            },
            {
              number: 3,
              correctAnswer: ["aorte thoracique descendante", "Aorte thoracique descendante"]
            },
            {
              number: 4,
              correctAnswer: ["aorte abdominale", "Aorte abdominale"]
            },
            {
              number: 5,
              correctAnswer: ["aorte sus-coronaire", "Aorte sus-coronaire"]
            },
            {
              number: 6,
              correctAnswer: ["racine aortique", "Racine aortique"]
            },
          ],
        },
        {
          id: 6,
          name: "Coupe de la peau",
          nbCorrection: 14,
          answers: [
            {
              number: 1,
              correctAnswer: ["épiderme", "Epiderme"]
            },
            {
              number: 2,
              correctAnswer: ["derme", "Derme"]
            },
            {
              number: 3,
              correctAnswer: ["hypoderme", "Hypoderme"]
            },
            {
              number: 4,
              correctAnswer: ["glande sébacée", "Glande sébacée", "glande sebacée", "Glande sebacée"]
            },
            {
              number: 5,
              correctAnswer: ["tissu conjonctif", "Tissu conjonctif"]
            },
            {
              number: 6,
              correctAnswer: ["cellules matricielles", "Cellules matricielles", "cellule matricielle", "Cellule matricielle"]
            },
            {
              number: 7,
              correctAnswer: ["terminaison nerveuse", "Terminaison nerveuse"]
            },
            {
              number: 8,
              correctAnswer: ["cellules adipeuses", "Cellules adipeuses", "cellule adipeuse", "Cellule adipeuse"]
            },
            {
              number: 9,
              correctAnswer: ["réseau artériel", "Réseau artériel", "reseau artériel", "Reseau artériel", "réseau arteriel", "Réseau arteriel", "reseau arteriel", "Reseau arteriel"]
            },
            {
              number: 10,
              correctAnswer: ["réseau veineux", "Réseau veineux", "reseau veineux", "Reseau veineux"]
            },
            {
              number: 11,
              correctAnswer: ["glande sudoripare exocrine", "Glande sudoripare exocrine"]
            },
            {
              number: 12,
              correctAnswer: ["muscle érecteur du poil", "Muscle érecteur du poil", "muscle erecteur du poil", "Muscle erecteur du poil"]
            },
            {
              number: 13,
              correctAnswer: ["capillaires", "Capillaires", "capillaire", "Capillaire"]
            },
            {
              number: 14,
              correctAnswer: ["pore de transpiration", "Pore de transpiration"]
            },
            {
              number: 15,
              correctAnswer: ["surface de la peau", "Surface de la peau"]
            },
            {
              number: 16,
              correctAnswer: ["pores", "Pores", "pore", "Pore"]
            },
            {
              number: 17,
              correctAnswer: ["tige d'un follicule pileux", "Tige d'un follicule pileux"]
            },
          ],
        },
        {
          id: 7,
          name: "Articulations mobiles",
          nbCorrection: 16,
          answers: [
            {
              number: 1,
              correctAnswer: ["articulation scapulo-humérale", "Articulation scapulo-humérale", "articulation scapulo-humerale", "Articulation scapulo-humerale"]
            },
            {
              number: 2,
              correctAnswer: ["articulation du genou", "Articulation du genou"]
            },
            {
              number: 3,
              correctAnswer: ["articulation coxo-fémorale", "Articulation coxo-fémorale", "articulation coxo-femorale", "Articulation coxo-femorale"]
            },
          ],
        },
        {
          id: 8,
          name: "Os et articulations du membre inférieur",
          nbCorrection: 18,
          answers: [
            {
              number: 1,
              correctAnswer: ["os coxal", "Os coxal"]
            },
            {
              number: 2,
              correctAnswer: ["hanche", "Hanche"]
            },
            {
              number: 3,
              correctAnswer: ["coxo-fémorale", "Coxo-fémorale"]
            },
            {
              number: 4,
              correctAnswer: ["fémur", "Fémur", "femur", "Femur"]
            },
            {
              number: 5,
              correctAnswer: ["patella", "Patella"]
            },
            {
              number: 6,
              correctAnswer: ["genou", "Genou"]
            },
            {
              number: 7,
              correctAnswer: ["tibia", "Tibia"]
            },
            {
              number: 8,
              correctAnswer: ["fibula", "Fibula"]
            },
            {
              number: 9,
              correctAnswer: ["malléole latérale", "Malléole latérale", "malleole latérale", "Malleole latérale", "malléole laterale", "Malléole laterale", "malleole laterale", "Malleole laterale"] 
            },
            {
              number: 10,
              correctAnswer: ["malléole médiale", "Malléole médiale", "malleole médiale", "Malleole médiale", "malléole mediale", "Malléole mediale", "malleole mediale", "Malleole mediale"]
            },
            {
              number: 11,
              correctAnswer: ["articulation de la cheville", "Articulation de la cheville", "cheville", "Cheville"]
            },
          ],
        },
        {
          id: 9,
          name: "Articulation du genou",
          nbCorrection: 20,
          answers: [
            {
              number: 1,
              correctAnswer: ["rotule", "Rotule"]
            },
            {
              number: 2,
              correctAnswer: ["membrane synoviale", "Membrane synoviale", "membrane sinoviale", "Membrane sinoviale"]
            },
            {
              number: 3,
              correctAnswer: ["tendon rotulien", "Tendon rotulien"]
            },
            {
              number: 4,
              correctAnswer: ["tibia", "Tibia"]
            },
            {
              number: 5,
              correctAnswer: ["cartilage", "Cartilage"]
            },
            {
              number: 6,
              correctAnswer: ["ménisque", "Ménisque", "menisque", "Menisque"]
            },
            {
              number: 7,
              correctAnswer: ["patella", "Patella"]
            },
          ],
        },
        {
          id: 10,
          name: "Crâne et Face (Vue latérale)",
          nbCorrection: 22,
          answers: [
            {
              number: 1,
              correctAnswer: ["os frontal", "Os frontal"]
            },
            {
              number: 2,
              correctAnswer: ["os sphénoïde", "Os sphénoïde", "os sphenoïde", "Os sphenoïde"]
            },
            {
              number: 3,
              correctAnswer: ["os malaire", "Os malaire"]
            },
            {
              number: 4,
              correctAnswer: ["os propre du nez", "Os propre du nez"]
            },
            {
              number: 5,
              correctAnswer: ["apophyse frontale du maxillaire", "Apophyse frontale du maxillaire"]
            },
            {
              number: 6,
              correctAnswer: ["apophyse caracoïde de la mandibule", "Apophyse caracoïde de la mandibule"]
            },
            {
              number: 7,
              correctAnswer: ["maxillaire supérieur", "Maxillaire supérieur", "maxillaire superieur", "Maxillaire superieur"]
            },
            {
              number: 8,
              correctAnswer: ["mandibule", "Mandibule"]
            },
            {
              number: 9,
              correctAnswer: ["apophyse mastoïde", "Apophyse mastoïde"]
            },
            {
              number: 10,
              correctAnswer: ["apophyse styloïde", "Apophyse styloïde"]
            },
            {
              number: 11,
              correctAnswer: ["os occipital", "Os occipital"]
            },
            {
              number: 12,
              correctAnswer: ["conduit auditif externe", "Conduit auditif externe"]
            },
            {
              number: 13,
              correctAnswer: ["os temporal", "Os temporal"]
            },
            {
              number: 14,
              correctAnswer: ["os pariétal", "Os pariétal", "os parietal", "Os parietal"]
            },
          ],
        },
        {
          id: 11,
          name: "Crâne et Face (Vue de face)",
          nbCorrection: 24,
          answers: [
            {
              number: 1,
              correctAnswer: ["frontal", "Frontal"]
            },
            {
              number: 2,
              correctAnswer: ["temporal", "Temporal"]
            },
            {
              number: 3,
              correctAnswer: ["zygomatique", "Zygomatique"]
            },
            {
              number: 4,
              correctAnswer: ["ethmoïde", "Ethmoïde"]
            },
            {
              number: 5,
              correctAnswer: ["mandibule", "Mandibule"]
            },
            {
              number: 6,
              correctAnswer: ["maxillaire", "Maxillaire"]
            },
            {
              number: 7,
              correctAnswer: ["sphénoïde", "Sphénoïde", "sphenoïde", "Sphenoïde"]
            },
            {
              number: 8,
              correctAnswer: ["pariétal", "Pariétal", "parietal", "Parietal"]
            },
            {
              number: 9,
              correctAnswer: ["lacrymal", "Lacrymal"]
            },
            {
              number: 10,
              correctAnswer: ["nasal", "Nasal"]
            },
          ],
        },
        {
          id: 12,
          name: "Colonne vertébrale (Vue latérale)",
          nbCorrection: 26,
          answers: [
            {
              number: 1,
              correctAnswer: ["moelle épinière", "Moelle épinière", "moelle epiniere", "Moelle epiniere", "moelle épiniere", "Moelle épiniere", "moelle epinière", "Moelle epinière"]
            },
            {
              number: 2,
              correctAnswer: ["racine nerveuse", "Racine nerveuse"]
            },
            {
              number: 3,
              correctAnswer: ["disque intervertébral", "Disque intervertébral", "disque intervertebral", "Disque intervertebral"]
            },
            {
              number: 4,
              correctAnswer: ["trou de conjugaison", "Trou de conjugaison"]
            },
            {
              number: 5,
              correctAnswer: ["vertèbres cervicales", "Vertèbres cervicales", "vertebres cervicales", "Vertebres cervicales", "vertèbre cervicale", "Vertèbre cervicale", "vertebre cervicale", "Vertebre cervicale"]
            },
            {
              number: 6,
              correctAnswer: ["vertèbres dorsales", "Vertèbres dorsales", "vertebres dorsales", "Vertebres dorsales", "vertèbre dorsale", "Vertèbre dorsale", "vertebre dorsale", "Vertebre dorsale"] 
            },
            {
              number: 7,
              correctAnswer: ["vertèbres lombaires", "Vertèbres lombaires", "vertebres lombaires", "Vertebres lombaires", "vertèbre lombaire", "Vertèbre lombaire", "vertebre lombaire", "Vertebre lombaire"]
            },
            {
              number: 8,
              correctAnswer: ["sacrum", "Sacrum"]
            },
            {
              number: 9,
              correctAnswer: ["coccyx", "Coccyx"]
            },
          ],
        },
        {
          id: 13,
          name: "Circulation sanguine",
          nbCorrection: 28,
          answers: [
            {
              number: 1,
              correctAnswer: ["lits capillaires des poumons", "Lits capillaires des poumons", "lit capillaires des poumons", "Lit capillaires des poumons", "lit capillaire des poumons", "Lit capillaire des poumons", "lits capillaire des poumons", "Lits capillaire des poumons"]
            },
            {
              number: 2,
              correctAnswer: ["veines pulmonaires", "Veines pulmonaires", "veine pulmonaires", "Veine pulmonaires", "veines pulmonaire", "Veines pulmonaire", "veine pulmonaire", "Veine pulmonaire"]
            },
            {
              number: 3,
              correctAnswer: ["aorte et ses rarnifications", "Aorte et ses rarnifications", "aorte", "Aorte"]
            },
            {
              number: 4,
              correctAnswer: ["lits capillaires des tissus", "Lits capillaires des tissus", "lit capillaires des tissus", "Lit capillaires des tissus", "lit capillaire des tissus", "Lit capillaire des tissus", "lits capillaire des tissus", "Lits capillaire des tissus"]
            },
            {
              number: 5,
              correctAnswer: ["ventricule gauche", "Ventricule gauche"]
            },
            {
              number: 6,
              correctAnswer: ["oreillette gauche", "Oreillette gauche"]
            },
            {
              number: 7,
              correctAnswer: ["ventricule droit", "Ventricule droit"]
            },
            {
              number: 8,
              correctAnswer: ["oreillette droite", "Oreillette droite"]
            },
            {
              number: 9,
              correctAnswer: ["veines caves", "Veines caves", "veine caves", "Veine caves", "veine cave", "Veine cave", "veines cave", "Veines cave"]
            },
            {
              number: 10,
              correctAnswer: ["artères pulmonaires", "Artères pulmonaires", "artère pulmonaires", "Artère pulmonaires", "artères pulmonaire", "Artères pulmonaire", "artère pulmonaire", "Artère pulmonaire", "arteres pulmonaires", "Arteres pulmonaires", "artere pulmonaires", "Artere pulmonaires", "arteres pulmonaire", "Arteres pulmonaire", "artere pulmonaire", "Artere pulmonaire"]
            },
          ],
        },
        {
          id: 14,
          name: "La cellule",
          nbCorrection: 30,
          answers: [
            {
              number: 1,
              correctAnswer: ["pore nucléaire", "Pore nucléaire", "pore nucleaire", "Pore nucleaire"]
            },
            {
              number: 2,
              correctAnswer: ["nucléole", "Nucléole", "nucleole", "Nucleole"]
            },
            {
              number: 3,
              correctAnswer: ["membrane nucléaire", "Membrane nucléaire", "membrane nucleaire", "Membrane nucleaire"]
            },
            {
              number: 4,
              correctAnswer: ["noyau", "Noyau"]
            },
            {
              number: 5,
              correctAnswer: ["réticulum endoplasmique rugueux", "Réticulum endoplasmique rugueux", "reticulum endoplasmique rugueux", "Reticulum endoplasmique rugueux"]
            },
            {
              number: 6,
              correctAnswer: ["réticulum endoplasmique lisse", "Réticulum endoplasmique lisse", "reticulum endoplasmique lisse", "Reticulum endoplasmique lisse"]
            },
            {
              number: 7,
              correctAnswer: ["centriole", "Centriole"]
            },
            {
              number: 8,
              correctAnswer: ["cytoplasme", "Cytoplasme"]
            },
            {
              number: 9,
              correctAnswer: ["membrane cytoplasme", "Membrane cytoplasme"]
            },
            {
              number: 10,
              correctAnswer: ["lysosome", "Lysosome"]
            },
            {
              number: 11,
              correctAnswer: ["mithochondrie", "Mithochondrie"]
            },
            {
              number: 12,
              correctAnswer: ["appareil de Golgi", "Appareil de Golgi"]
            },
            {
              number: 13,
              correctAnswer: ["ribosome", "Ribosome"]
            },
            {
              number: 14,
              correctAnswer: ["réticulum endoplasmique rugueux", "Réticulum endoplasmique rugueux", "reticulum endoplasmique rugueux", "Reticulum endoplasmique rugueux"]
            },
          ],
        },
        {
          id: 15,
          name: "Os et articulations du membre supérieur",
          nbCorrection: 32,
          answers: [
            {
              number: 1,
              correctAnswer: ["épaule", "Epaule", "epaule"]
            },
            {
              number: 2,
              correctAnswer: ["membre supérieur", "Membre supérieur", "membre superieur", "Membre superieur"]
            },
            {
              number: 3,
              correctAnswer: ["bras", "Bras"]
            },
            {
              number: 4,
              correctAnswer: ["avant-bras", "Avant-bras"] 
            },
            {
              number: 5,
              correctAnswer: ["main", "Main"]
            },
            {
              number: 6,
              correctAnswer: ["os carpiens", "Os carpiens", "os carpien", "Os carpien"]
            },
            {
              number: 7,
              correctAnswer: ["os métacarpiens", "Os métacarpiens", "os metacarpiens", "Os metacarpiens", "os métacarpien", "Os métacarpien", "os metacarpien", "Os metacarpien"]
            },
            {
              number: 8,
              correctAnswer: ["phalanges proximale médiale et distale", "Phalanges proximale médiale et distale", "phalanges proximale mediale et distale", "Phalanges proximale mediale et distale", "phalange", "Phalange", "phalanges", "Phalanges"]
            },
            {
              number: 9,
              correctAnswer: ["clavicule", "Clavicule"]
            },
            {
              number: 10,
              correctAnswer: ["omoplate", "Omoplate"]
            },
            {
              number: 11,
              correctAnswer: ["scapulo humérale", "Scapulo humérale", "scapulo humerale", "Scapulo humerale"]
            },
            {
              number: 12,
              correctAnswer: ["humérus", "Hmérus", "humerus", "Humerus"]
            },
            {
              number: 13,
              correctAnswer: ["radius", "Radius"]
            },
            {
              number: 14,
              correctAnswer: ["ulna", "Ulna"]
            },
            {
              number: 15,
              correctAnswer: ["jointure acromioclaviculaire", "Jointure acromioclaviculaire"]
            },
            {
              number: 16,
              correctAnswer: ["jointure de l'humérus", "Jointure de l'humérus", "jointure de l'humerus", "Jointure de l'humerus"]
            },
            {
              number: 17,
              correctAnswer: ["coude", "Coude"]
            },
            {
              number: 18,
              correctAnswer: ["jointures huméroradiale", "Jointures huméroradiale", "jointures humeroradiale", "Jointures humeroradiale", "jointure huméroradiale", "Jointure huméroradiale", "jointure humeroradiale", "Jointure humeroradiale"]
            },
            {
              number: 19,
              correctAnswer: ["humérocubitale", "Humérocubitale", "humerocubitale", "Humerocubitale"] 
            },
            {
              number: 20,
              correctAnswer: ["radiocubitale proximale", "Radiocubitale proximale"]
            },
            {
              number: 21,
              correctAnswer: ["jointure radiocubitale distale", "Jointure radiocubitale distale"]
            },
            {
              number: 22,
              correctAnswer: ["jointure radiocarpiale", "Jointure radiocarpiale"]
            },
            {
              number: 23,
              correctAnswer: ["jointures micarpiales", "Jointures micarpiales", "jointure micarpiales", "Jointure micarpiales", "jointures micarpiale", "Jointures micarpiale", "jointure micarpiale", "jointure micarpiale"]
            },
            {
              number: 24,
              correctAnswer: ["jointures carpiométacarpiales", "Jointures carpiométacarpiales", "jointure carpiométacarpiales", "Jointure carpiométacarpiales", "jointures carpiométacarpiale", "Jointures carpiométacarpiale", "jointure carpiométacarpiale", "jointure carpiométacarpiale", "jointures carpiometacarpiales", "Jointures carpiometacarpiales", "jointure carpiometacarpiales", "Jointure carpiometacarpiales", "jointures carpiometacarpiale", "Jointures carpiometacarpiale", "jointure carpiometacarpiale", "jointure carpiometacarpiale"]
            },
            {
              number: 25,
              correctAnswer: ["jointures métacarpiophalangiennes", "Jointures métacarpiophalangiennes", "jointure métacarpiophalangiennes", "Jointure métacarpiophalangiennes", "jointures métacarpiophalangienne", "Jointures métacarpiophalangienne", "jointure métacarpiophalangienne", "jointure métacarpiophalangienne", "jointures metacarpiophalangiennes", "Jointures metacarpiophalangiennes", "jointure metacarpiophalangiennes", "Jointure metacarpiophalangiennes", "jointures metacarpiophalangienne", "Jointures metacarpiophalangienne", "jointure metacarpiophalangienne", "jointure metacarpiophalangienne"]
            },
            {
              number: 26,
              correctAnswer: ["jointures interphalangienne proximales", "Jointures interphalangienne proximales", "jointure interphalangienne proximales", "Jointure interphalangienne proximales", "jointures interphalangienne proximale", "Jointures interphalangienne proximale", "jointure interphalangienne proximale", "Jointure interphalangienne proximale"]
            },
            {
              number: 27,
              correctAnswer: ["jointures interphalangienne distales", "Jointures interphalangienne distales", "jointure interphalangienne distales", "Jointure interphalangienne distales", "jointures interphalangienne distale", "Jointures interphalangienne distale", "jointure interphalangienne distale", "Jointure interphalangienne distale"]
            },
          ],
        },
        {
          id: 16,
          name: "Fosses nasales",
          nbCorrection: 34,
          answers: [
            {
              number: 1,
              correctAnswer: ["sinus sphénoïde", "Sinus sphénoïde", "sinus sphenoïde", "Sinus sphenoïde"]
            },
            {
              number: 2,
              correctAnswer: ["narine interne", "Narine interne"]
            },
            {
              number: 3,
              correctAnswer: ["nasopharynx", "Nasopharynx"] 
            },
            {
              number: 4,
              correctAnswer: ["narine externe", "Narine externe"]
            },
            {
              number: 5,
              correctAnswer: ["cornet nasal inférieur", "Cornet nasal inférieur", "cornet nasal inferieur", "Cornet nasal inferieur"]
            },
            {
              number: 6,
              correctAnswer: ["cornet nasal moyen", "Cornet nasal moyen"]
            },
            {
              number: 7,
              correctAnswer: ["sinus frontal", "Sinus frontal"]
            },
            {
              number: 8,
              correctAnswer: ["cornet nasal supérieur", "Cornet nasal supérieur", "cornet nasal superieur", "Cornet nasal superieur"]
            },
          ],
        },
        {
          id: 17,
          name: "La fonction urinaire",
          nbCorrection: 36,
          answers: [
            {
              number: 1,
              correctAnswer: ["artère rénale", "Artère rénale", "artere rénale", "Artere rénale", "artère renale", "Artère renale", "artere renale", "Artere renale"]
           },
           {
              number: 2,
              correctAnswer: ["rein gauche", "Rein gauche"]
           },
           {
              number: 3,
              correctAnswer: ["uretère gauche", "Uretère gauche", "uretere gauche", "Uretere gauche"]
           },
           {
              number: 4,
              correctAnswer: ["artère aorte", "Artère aorte", "artere aorte", "Artere aorte"]
           },
           {
              number: 5,
              correctAnswer: ["vessie", "Vessie"]
           },
           {
              number: 6,
              correctAnswer: ["urètre", "Urètre", "uretre", "Uretre"]
           },
           {
              number: 7,
              correctAnswer: ["orifice urogénital", "Orifice urogénital", "orifice urogenital", "Orifice urogenital"]
           },
           {
              number: 8,
              correctAnswer: ["uretère droit", "Uretère droit", "uretere droit", "Uretere droit"]
           },
           {
              number: 9,
              correctAnswer: ["veine cave inférieure", "Veine cave inférieure", "veine cave inferieure", "Veine cave inferieure"]
           },
           {
              number: 10,
              correctAnswer: ["rein droit", "Rein droit"]
           },
           {
              number: 11,
              correctAnswer: ["veine rénale", "Veine rénale", "veine renale", "Veine renale"]
           },
          ]
        },
        {
          id: 18,
          name: "Appareil urinaire",
          nbCorrection: 38,
          answers: [
            {
              number: 1,
              correctAnswer: ["veine cave inférieure", "Veine cave inférieure", "veine cave inferieure", "Veine cave inferieure"]
           },
           {
              number: 2,
              correctAnswer: ["glande surrênale droit", "Glande surrênale droit", "glande surrenale droit", "Glande surrenale droit", "glande surrénale droit", "Glande surrénale droit"]
           },
           {
              number: 3,
              correctAnswer: ["rein droit", "Rein droit"]
           },
           {
              number: 4,
              correctAnswer: ["veine rénale", "Veine rénale", "veine renale", "Veine renale"]
           },
           {
              number: 5,
              correctAnswer: ["bassinet", "Bassinet"]
           },
           {
              number: 6,
              correctAnswer: ["uretère droit", "Uretère droit", "uretere droit", "Uretere droit"]
           },
           {
              number: 7,
              correctAnswer: ["méat urinaire", "Méat urinaire", "meat urinaire", "Meat urinaire"]
           },
           {
              number: 8,
              correctAnswer: ["vessie", "Vessie"]
           },
           {
              number: 9,
              correctAnswer: ["artère et veine iliaques internes", "Artère et veine iliaques internes", "artere et veine iliaques internes", "Artere et veine iliaques internes", "artère + veine iliaques internes", "Artère + veine iliaques internes", "artere + veine iliaques internes", "Artere + veine iliaques internes", "artère+veine iliaques internes", "Artère+veine iliaques internes", "artere+veine iliaques internes", "Artere+veine iliaques internes", "artère iliaque interne", "Artère iliaque interne", "artere iliaque interne", "Artere iliaque interne", "veine iliaque interne", "Veine iliaque interne"]
           },
           {
              number: 10,
              correctAnswer: ["artère et veine iliaques externes", "Artère et veine iliaques externes", "artere et veine iliaques externes", "Artere et veine iliaques externes", "artère + veine iliaques externes", "Artère + veine iliaques externes", "artere + veine iliaques externes", "Artere + veine iliaques externes", "artère+veine iliaques externes", "Artère+veine iliaques externes", "artere+veine iliaques externes", "Artere+veine iliaques externes", "artère iliaque externe", "Artère iliaque externe", "artere iliaque externe", "Artere iliaque externe", "veine iliaque externe", "Veine iliaque externe"]
           },
           {
              number: 11,
              correctAnswer: ["artère et veine iliaques communes", "Artère et veine iliaques communes", "artere et veine iliaques communes", "Artere et veine iliaques communes", "artère + veine iliaques communes", "Artère + veine iliaques communes", "artere + veine iliaques communes", "Artere + veine iliaques communes", "artère+veine iliaques communes", "Artère+veine iliaques communes", "artere+veine iliaques communes", "Artere+veine iliaques communes", "artère iliaque commune", "Artère iliaque commune", "artere iliaque commune", "Artere iliaque commune", "veine iliaque commune", "Veine iliaque commune"]
           },
           {
              number: 12,
              correctAnswer: ["uretère gauche", "Uretère gauche", "uretere gauche", "Uretere gauche"]
           },
           {
              number: 13,
              correctAnswer: ["artère rénale", "Artère rénale", "artere rénale", "Artere rénale", "artère renale", "Artère renale", "artere renale", "Artere renale"]
           },
           {
              number: 14,
              correctAnswer: ["rein gauche", "Rein gauche"]
           },
           {
              number: 15,
              correctAnswer: ["glande surrênale gauche", "Glande surrênale gauche", "glande surrenale gauche", "Glande surrenale gauche", "glande surrénale gauche", "Glande surrénale gauche"]
           },
           {
              number: 16,
              correctAnswer: ["aorte descendante", "Aorte descendante"]
           },
           {
              number: 17,
              correctAnswer: ["veine cave", "Veine cave"]
           },
           {
             number: 18,
             correctAnswer: ["aorte abdominale", "Aorte abdominale"]
           }
          ]
        },
        {
          id: 19,
          name: "Le néphron",
          nbCorrection: 40,
          answers: [
            {
              number: 1,
              correctAnswer: ["tube contourné proximal", "Tube contourné proximal"]
           },
           {
              number: 2,
              correctAnswer: ["tube contourné distal", "Tube contourné distal"]
           },
           {
              number: 3,
              correctAnswer: ["autre néphron", "Autre néphron"]
           },
           {
              number: 4,
              correctAnswer: ["tube collecteur de Bellini", "Tube collecteur de Bellini", "tube collecteur de bellini", "Tube collecteur de bellini"]
           },
           {
              number: 5,
              correctAnswer: ["branche ascendante de la branche de henlé", "Branche ascendante de la branche de henlé", "tubule", "Tubule"]
           },
           {
              number: 6,
              correctAnswer: ["anse de henlé", "Anse de henlé"]
           },
           {
              number: 7,
              correctAnswer: ["veine rénale", "Veine rénale", "veine renale", "Veine renale"]
           },
           {
              number: 8,
              correctAnswer: ["artériole rénale", "Artériole rénale", "arteriole rénale", "Arteriole rénale", "artériole renale", "Artériole renale", "arteriole renale", "Arteriole renale"]
           },
           {
              number: 9,
              correctAnswer: ["glomérule", "Glomérule", "glomerule", "Glomerule"]
           },
           {
              number: 10,
              correctAnswer: ["capsule de Bowman", "Capsule de Bowman", "capsule de bowman", "Capsule de bowman"]
           }
          ]
        }
      ],
      displayText: true,
      choiceOnePic: false,
      randomPic: false,
    };
  },
  methods: {    
    showOnePic() {
      this.choiceOnePic = true;
      this.displayText = !this.displayText;
    },
    showRandomPic() {
      this.randomPic = true;
      this.displayText = !this.displayText;
    },
  },
};
</script>

<style>
@import "https://fonts.googleapis.com/css?family=Open+Sans+Condensed:300";
.box-3 {
  height: 33.33%;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 30px;
}

.btn {
  line-height: 50px;
  height: 50px;
  text-align: center;
  width: 150px;
  cursor: pointer;
}

/* 
========================
      BUTTON THREE
========================
*/
.btn-three {
  color: #c7c7c7;
  transition: all 0.5s;
  position: relative;
}
.btn-three::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 1;
  background-color: rgba(255, 255, 255, 0.1);
  transition: all 0.3s;
}
.btn-three:hover::before {
  opacity: 0;
  transform: scale(0.5, 0.5);
}
.btn-three::after {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 1;
  opacity: 0;
  transition: all 0.3s;
  border: 1px solid rgba(255, 255, 255, 0.5);
  transform: scale(1.2, 1.2);
}
.btn-three:hover::after {
  opacity: 1;
  transform: scale(1, 1);
}
.divChoose {
  position: absolute;
  top: 14%;
  left: 20%;
  right: 55%;
  border: 2px solid black;
  padding: 10px 20px 15px 20px;
  text-align: justify;
}
.divRandom {
  position: absolute;
  top: 14%;
  left: 55%;
  right: 20%;
  border: 2px solid black;
  padding: 10px 20px 15px 20px;
  text-align: justify;
}

.imgList {
  width: 15%;
}
</style>