# Land-Registry-Smart-Contract
we make Ethereum based Land Registry. 
// SPDX-License-Identifier: MIT
pragma solidity >=0.7.0 <0.9.0;

contract Landregistration
{
    struct Landreg
    {
        uint LandID;
        string Area;
        string city;
        string state;
        uint LandPrice;
        uint propertyPID;
        
    }
}
   struct BuyerDetail
   {
       string Name;
       uint Age;
       string city;
       string state;
       uint LandPrice;
       uint propertyPID;
       


   }

   struct BuyerDetail
   {
       string Name;
       uint Age;
       string city;
       string state;
       uint LandPrice;
       uint PropertPID;
       
   }

   struct BuyerDetail
   {
       string Name;
       uint Age;
       string city;
       string  CNIC;
       string Email;
       
   }

   struct sellerDetail
   {
       uint ID;
       string Name;
       uint age;
       string city;
       string CNIC;
       string Email;

   }
    
    struct LandInspectorDetail
    {
        address ID;
        string Name;
        uint age;
        string Designation;

    }

    mapping(uint => LandRegistration) public LandRegistration;
    mapping(address =>  BuyerDetail) public BuyerDetails;
    mapping(address =>  SellerDetail) public SellerDetails;
    mapping(address =>  LandInspectorDetail) public LandInspectorDetails;
    mapping(address => bool) public BuyerVerify;
    mapping(address => bool) public SellerVerify;
    mapping(uint => bool) public LandVerify;
    mapping(address => bool) public LanddInspectorVerify;

    //Function of register seller

    function RegisterSeller(address addr,uint ID, string memory NAME, uint Age, string memory city, string memory CNIC, string  memory Email) public
    
    {
        SellerDetails[addr] = SellerDetail(ID, NAME, AGE, CITY, CNIC, Email);
        SellerVerify[addr]= false;
    }
     // Function of verify seller
     function verifySeller(address addr) public
     {
         sellerVerify[addr] = true;
     }
      // Function of reject seller

    
        function RejectSeller(address addr) public
    {
        SellerVerify[addr] = false;
    }
    // Function of register Buyer

    function RegisterBuyer(string memory NAME, uint AGE, string memory CITY, string memory CNIC, string memory Email) public
    {
        BuyerDetails[msg.sender] = BuyerDetail( NAME, AGE, CITY, CNIC, Email);

        BuyerVerify[msg.sender] = false;

    }
    //function of verify buyer

    function VerifyBuyer(address add) public
    {
        BuyerVerify[addr] = true;

    }
    //functio of reject buyer

    function RejectBuyer(address addr) public
    {
        BuyerVerify[addr] = false;
    }
    //function  of land registration

    function RegisterLand(uint LandID, string memory Area, string memory city, string memory state, uint Landprice, uint PropertyPID, address Owner, address CurrentOwner) public

    {
        LandDetails[LandID] = Landreg(LandID. Area, city, state, LandPrice, PropertPID, Owner, CurrentOwner);
        LandVerify[LandID] = false;

    }
    // function of land Verify
    function VerifyLand(uint LandID) public
    {
        LandVerify[LandID] = true;
    }
    //function of reject land
    function RejectLand(uint LandID) public
    {
        LandVerify[LandID] = false;
    
    }
    //seller update

    function SellerUpdate(address addr, string memory Name, uint Age, string memory City, string memory CNIC, string memory Email) public
    {
       SellerDetails[addr].Name=Name_;
       SellerDetails[addr].Age=Age_;
       SellerDetails[addr].City=City_;
       SellerDetails[addr].CNIC=CNIC_;
       SellerDetails[addr].Email=Email_;

    }
    //Buyer update
    function BuyerUpdate(address addr, string memory Name, uint Age, string memory City, string memory CNIC, string memory Email) public
    {
       BuyerDetails[addr].Name=Name_;
       BuyerDetails[addr].Age=Age_;
       BuyerDetails[addr].City=City_;
       BuyerDetails[addr].CNIC=CNIC_;
       BuyerDetails[addr].Email=Email_;

    }
    //Land Details 
    function getLandDetails (uint ID) Public view returns (uint, string memory, string memory, string memory, string memory, string memory )public

    {
        return (
            LandDetails[ID].LandID, LandDetails[ID].Area, LandDetails[ID].City, LandDetails[ID].State, LandDetails[ID].LandPrice, 
            LandDetails[ID].PropertyPID);

        )
    }
    
    //Owner Details
  
    function getLandOwner (uint LandID) Public view returns(address)
    {
        return LandDetails[LandID].Owner;

    }

    //Current Owner Details

    function getCurrentLandOwner(uint LandID) Public view returns(address)
    {
        return LandDetails[LandID].CurrentOwner;

    }

    //City Details
    
    function getLandCity(uint ID) public view returns (string memory)
    {
        return (LandDetails[ID].city);
    }
    
    //Land Price Details 

    function getLandPrice(uint ID) Public view returns(uint)
    {
        return (LandDetails[ID].LandPrice);
    }

    //Area Details land ID

    function   getLandArea(uint ID) public view returns (string memory)
    {
        return (LandDetails[ID].Area);
    }

    //Function of Register Land Inspector

    function RegisterLandInspector  (address add, address ID, string memory Name, uint Age, string memory Designation) public

    {
        LandInspectorDetails[add] = LandInspectorDetail(ID, Name, Age, Designation);

        Landinspectorverify [addr] = true;

    }

    //Function of verify land inspector

    function verifyLandInspector(address add) public
    {
        Landinspectorverify [addr] = true;
    }

    //Function of reject land inspector

    function rejectLandInspector)Address add) public
    {
         Landinspectorverify [addr] = false;
    }

   

