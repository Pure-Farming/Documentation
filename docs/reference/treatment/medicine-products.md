---
title: Medicine Products
menu_order: 1
post_status: publish
post_excerpt: Reference Data - Medicine Products
taxonomy:
  category:
    - root
  post_tag:
    - root
---

# Reference Data: Medicine

## Data Returned

A call to the Medicine API returns the following fields.


| **Response item** | **Description**           | **Data type** |
| ----------------- | --------------------------| ------------- |
| **form**| The physical form of a dose of the medicine.  Enumeration modified from the PubCRIS database.| Enumeration medicine-form|
| **registrant**| The registering company or manufacturer of the medicine| String|
| **registrationDate**| The date the medicine was registered in the scheme| Date/Time|
| **expiryDate**| The date the registration of the medicine in the scheme expires.| Date/Time|
| **classification**| The classification or type of medicine.   Enumeration modified from the PubCRIS database.| Enumeration medicine-classification |
| **species**| The species that may be treated by this medicine.| Array icarAnimalSpecieType|
| **activeIngredients**| The active ingredients in the medicine.| Array medicine-ingredient-type |
| **withholdings**| The withholding periods defined for this medicine for a species for a particular product or food item. | Array medicine-withholding-type|


## Enumerations

Type: medicine-form

Values:

  Aerosol
  AqueousConcentrate
  AqueousSuspension
  AqueousSuspensionWithMicroencapsulatedActive
  AqueousTopicalSolution
  Aural-Ophthalmic-Oro/NasoPharyngeal
  Backline
  Bait
  BaitConcentrate
  BlendingConcentrate
  Block(Inc.Stick)
  Briquet
  CapsuleSuspension
  Cartridge
  Collar-Medalion
  Cream
  DermalPaste+OralPaste
  Diagnostic
  DispersibleConcentrate
  DryFlowable
  Dust
  DustablePowder
  EarTag
  EmulsifiableConcentrate
  EmulsifiableConcentrate+DryFlowable
  EmulsifiableGranule
  EmulsifiableSuspension
  Emulsion
  Emulsion-OilInWater
  EncapsulatedGranule
  FineGranule
  FishTankMedication
  Gas(SoilFumigant)
  GasGeneratingProduct
  Gel
  GeneticMaterial
  GranularFormulation
  ImpregnatedPlasticStrips
  ImpregnatedWetTissue
  Injection
  Intra-Mammary
  Intra-RuminalDevice
  Intra-Vaginal/UterinePrep/Device
  LaminatedBlanket
  Liquid
  LiquidConcentrate
  LiquidVaporiser
  LiquifiedGas
  Lotion
  MatrixReleaseFormulation
  MedicatedDressing-TopicalDevice
  MicroEmulsifiableConcentrate
  MicroEmulsion
  Microencapsulated
  MicroencapsulatedGel
  MicroencapsulatedPaste
  Microgranule
  MixedFormulationOfCapsuleSuspensionAndSuspensionConcentrate
  MixedFormulationOfCsAndEw
  Non-AqueousConcentrate
  OilMiscibleLiquid
  Oil-BasedSuspensionConcentrate
  Oil-BasedSuspensionConcentrates
  Ointment(Inc.Lotion-Salve-Dressing)
  OralBlock-Lick
  OralBolus+IntraVaginal/Uterine
  OralBolus-Chewable
  OralBolus/Chewable+TopicalSolution/Suspension
  OralCapsule
  OralChewable+TopicalCream-Ointment-Paste-Gel
  OralFood(Can/Semi-Dry/Dry)
  OralGel
  OralGranules-Pellets
  OralPaste
  OralPowder-Pre-Mix
  OralSeleniumFertilizer
  OralSolution/Suspension
  OralSyrup
  OralTablet
  OralTablet+TopicalSolution
  OtherLiquidsToBeAppliedUndiluted
  Paint
  ParenteralImplant-Device
  ParenteralLiquid/Solution/Suspension
  Paste
  Pellet(EgSnailBait)
  Powder
  PowderForDrySeedTreatment
  PressurisedGas
  PressurisedSpray
  Ready-To-UseBait
  RectalSuppository
  Resin
  Sachet
  Shampoo
  SlowReleaseGenerator(Inc.FleaCollars)
  SmokeGenerator(FumigantInsectOrFungicide)
  Soap
  Soap(Inc.Shampoo)
  Solid(Inc.MosquitoCoilsAndCandles-Premixes)
  SolubleConcentrate
  SolublePowder
  SolutionForSeedTreatment
  SuspensionConcentrate
  SuspensionConcentratesForSeedTreatment(FS)
  Suspoemulsion
  Tablet(Inc.Pellet-Bolus-Suppository-Capsule)
  TabletsForDirectApplication
  Topical+OralSolution/Suspension
  TopicalAerosolSpray
  TopicalCream-Ointment-Paste-Gel-Lotion
  TopicalDust-Powder
  TopicalPumpSpray
  TopicalSoln+Aural-Opthal-Oro
  TopicalSolution/Suspension
  TopicalSpray+Lotion
  ToweletWithImpregnatedLiquid
  TrackingPowder
  TransgenicPlant
  TreatedApparelAndGear
  UltraLowVolume
  VaccineOrAntisera
  VaccinesOrAntiSera
  VapourReleasingProduct
  Vet*
  VeterinaryInhalationAnaesthetics
  WaterDispersibleGranule
  WaterDispersibleGranule+AqueousConcentrate
  WaterMiscibleLiquid
  WaterSolubleGels
  WaterSolubleGranules
  WaxBlock
  WettablePowder

Type: medicine-classification

values:

  ActiveConstituent
  AlimentarySystem
  Anaesthetics/Analgesics
  Antibiotic+Related
  Antibiotic+Nutritional
  Antibiotic+Genitourinary
  Antidotes
  Antihistamines
  BrandingSubstance
  CentralNervousSystem
  Dermal+EquipDisinfectant
  DermatologicalPreparations
  Disinfectant
  EndocrineSystem
  Euthanasiates
  GenitourinarySystem
  Immuno+Parasite+Nutrition
  Immunotherapy
  MusculoskeletalSystem
  Nutrition+Metabolism
  OphthalmicPreparations
  Parasiticide+Nutritional
  Parasiticides







Follow output data api convention for database queries

Most likely 3 endpoints (and possibly additional OGC ones if it is geospatial data)

Need to determine if there are any optional query string filters to be applied for the specific resource type
i.e. for crop/work-record

/reference/livestock/treatment/medicine-products
Criteria for finding medicine products:
I want a medicine by country (registration scheme)
I want a medicine by species (eg cattle sheep)
I want a medicine by specification (eg antibiotics pesticides etc)
Can apply multiple filters
/reference/livestock/treatment/medicine-products/{scheme id}
/reference/livestock/treatment/medicine-products/{name-contains}

1. Add BaseResourceType in mediatr
   a. Dapper Query that queries the view
   b. Model that represents the raw query
2. Add Mediatr queries for each endpoint
3. Add controller methods
4. Add comments to output objects / methods for swagger

Notes:
Use the MoA.Platform.Schema nuget package for the output models
Use the MoA.Platform.Persistance nuget package for enum mapping for the dapper query

Query DB through the DB context similar to existing ref handler methods