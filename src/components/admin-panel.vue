<template>
  <div class="body">
    <v-data-table
    @click:row="showModal"
    :disable-sort = true
    :headers="headers"
    :items="companies"
    item-key="name"
    class="elevation-1"
    :search="search"
  >
    <template v-slot:top>
        <v-text-field
          v-model="search"
          label="Search"
          class="mx-4"
        ></v-text-field>
    </template>
    <template v-slot:item.approved="{item}">
        <i class="fa fa-check-circle check-circle" :class="{approved: item.approved}"></i>
    </template>
  </v-data-table>
  <div class="text-center">
    <v-dialog
      v-model="dialog"
      width="850"
    >
      <v-card>
        <v-card-title class="headline white lighten-3">
          {{currentRow.name}}
          <i class="fa fa-check-circle check-circle" :class="{approved: currentRow.approved}"></i>
        </v-card-title>
        <v-card-text class="dialog">
          <div class="card-section-top">
            <div class="industry-section details-section">
              <span class="card-infos">Industry</span><br>
              <span class="card-details">{{currentRow.industry}}</span>
            </div>
            <div class="contact-person-section details-section">
              <span class="card-infos">Contact person</span><br>
              <span class="card-details">{{currentRow.contactPerson}}</span>
            </div>
          </div>
          <div class="card-section-middle">
            <div class="contact-section details-section">
              <span class="card-infos">Contact</span><br>
              <span class="card-details">{{currentRow.contact}}</span>
            </div>
            <div class="comp-registration details-section">
              <span class="card-infos">Company Registration No</span><br>
              <span class="card-details">{{currentRow.companyRegistrationNo}}</span>
            </div>
          </div>
          <div class="card-section-bottom">
            <div class="email-section">
              <i class="fas fa-envelope"></i>
              <span class="card-details">{{currentRow.email}}</span>
            </div>
            <div class="call-section">
              <i class="fas fa-phone-alt"></i>
              <span class="card-details">{{currentRow.telephone}}</span>
            </div>
            <div>
              <i class="fa fa-print"></i>
              <span class="card-details">{{currentRow.fax}}</span>
            </div>
          </div>
           <div class="addres-section">
              <i class="fas fa-map-marker-alt"></i>
              <span class="card-details">{{currentRow.address}}</span>
            </div>
        </v-card-text>
        <v-divider></v-divider>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn class="approve-button"
            color="primary"
            elevation="2"
            v-if="!currentRow.approved"
            text
            @click="approve"
          >
            Approve
          </v-btn>
          <v-btn
            color="red"
            text
            @click="dialog = false"
          >
            Close
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </div>
  </div>
</template>
<script>
  export default {
    data: () => ({
      search: '',
      dialog: false,
      name: 'PPIPBM',
      address: "Suite 9-5 & 9-6, Aras 9, Menara Matrade West Wing,Malaysia",
      telephone: +60362032727,
      fax: +60362032626,
      email: "secretariat.ppipbm@gmail.com",
      contactPerson: +60362032930,
      contact: +60362032931,
      companyRegistrationNo: "(PPM-007-14-27061 987)",
      industry:"Nonprofit Organizations",
      companies: [
        {
          approved: false,
          name: 'PPIPBM',
          address: "Suite 9-5 & 9-6, Aras 9, Menara Matrade West Wing,Malaysia",
          telephone: "+60362032727",
          fax: "+60362032626",
          email: "secretariat.ppipbm@gmail.com",
          contactPerson: "John Doe",
          contact: "+60362032931",
          companyRegistrationNo: "(PPM-007-14-27061 987)",
          industry:"Nonprofit Organizations"        
        },
        {
          approved: true,
          name: 'Miss Elwani',
          address: "Suite 3, Sentral Business Suites @Kompleks Sentral Point,Malaysia",
          telephone:" +60193684465",
          fax:" +60193684688",
          email: "info@misselwani.com",
          contactPerson: "Kyle",
          contact:" +60193684685",
          companyRegistrationNo: "H-123456",
          industry:"Health, Wellness and Fitness"        
        },
        {
          approved: false,
          name: 'KATTA KAYU',
          address: "LG-32&33, Cheras Sentral Mall,Malaysia",
          telephone: "03 - 89589210",
          fax: "03 - 89589211",
          email: "kattakayu@gmail.com",
          contactPerson: "Pedro",
          contact: "03 - 89589215",
          companyRegistrationNo: "T-123456",
          industry:"Furniture"        
        },
        {
          approved: false,
          name: 'Bumi Nilam Sdn Bhd',
          address: "No 37 Ground Floor, Jalan Puteri 1/8, Bandar Puteri, 47100, Puchong, Malaysia",
          telephone: "+60380669988",
          fax: "+60380669968",
          email: "sales@buminilam.com",
          contactPerson: "Warren",
          contact: "+60380669981",
          companyRegistrationNo: "882402-W",
          industry:"Security Equipment & Services"        
        },
        {
          approved: false,
          name: 'Canali',
          address: "2.51.00, Level 2, Selangor, Malaysia",
          telephone: "+60321449902",
          fax: "+60321449901",
          email: "support@canali.com",
          contactPerson: "Shirley",
          contact: "+60321449910",
          companyRegistrationNo: "10101-W",
          industry:"Consumer Goods"        
        },
          {
          approved: false,
          name: 'ADRIANA',
          address: "Lot 2.40 & 2.41, Second Floor, Kota Bahru Mall, Jalan Hamzah,, Kota Bahru, Malaysia",
          telephone: "+60333347787",
          fax: "+60333347788",
          email: "support@adrianaclothing.com",
          contactPerson: "Vernon",
          contact: "+60333347685",
          companyRegistrationNo: "888412-W",
          industry:"Apparel & Fashion"        
        },
           {
          approved: false,
          name: 'Amira\'s Cosmetics',
          address: "A 14/1, 1, Jalan Ampang Utama 2/2, Taman Ampang Utama, Kuala Lumpur, Malaysia",
          telephone: "+60355583645",
          fax: "+60355583546",
          email: "amiracosmetic@gmail.com",
          contactPerson: "Lucas",
          contact: "+60355583641",
          companyRegistrationNo: "958420-W",
          industry:"Consumer Goods"        
        },
        {
          approved: false,
          name: 'Basement Apes Studio',
          address: "Level B3, One Utama, Lot S327, City Centre No1, Bandar Utama,, Petaling Jaya, Malaysi",
          telephone: "+60358325912",
          fax: "+60358325811",
          email: "basementapes@gmail.com",
          contactPerson: "Cole",
          contact: "+60358325818",
          companyRegistrationNo: "888402-W",
          industry:"Media & Media Production"        
        },
        {
          approved: false,
          name: 'Rasa Malaysia',
          address: "B-15-3, Level 15, Tiara Tower, 1 Lorong Tun Hussien Onn 50000, Kuala Lumpur, Malaysia",
          telephone: "+60321449902",
          fax: "+60321449900",
          email: "rasamalaysia@gmail.com",
          contactPerson: "James",
          contact: "+60321449909",
          companyRegistrationNo: "912231-W",
          industry:"Food & Beverages"        
        },
          {
          approved: false,
          name: 'Farm Fresh Sdn Bhd',
          address: "Farm Fresh, Petaling Jaya, Malaysia",
          telephone: "+60321441498",
          fax: "+60321442243",
          email: "contact@ukyone.com",
          contactPerson: "Sarah",
          contact: "+60321443176",
          companyRegistrationNo: "W-102020",
          industry:"Food & Beverages"        
        },
        {
          approved: false,
          name: 'Digi.Com Berhad',
          address: "10, Jalan Delima 1/1, Subang Hi-tech Industrial Park,, Subang Jaya, Malaysia",
          telephone: "+6037584838",
          fax: "+6037584636",
          email: "contact@ukyone.com",
          contactPerson: "Brenda jackson",
          contact: "+6037584030",
          companyRegistrationNo: "0201283M",
          industry:"Telecommunications"        
        },
          {
          approved: false,
          name: 'Accenture',
          address: "The Gardens North Tower, 35, Lingkaran Syed Putra,, Kuala Lumpur, Malaysia",
          telephone: "+60122177123",
          fax: "+60122177124",
          email: "support@accenture.com",
          contactPerson: "Isaac",
          contact: "+60122177223",
          companyRegistrationNo: "10101232-W",
          industry:"Information Technology and Services"        
        }, 
        {
          approved: false,
          name: 'RC Supplements',
          address: "8, Greatest street, Olymp mountain, Metroflex Gym, United States",
          telephone: "+1234567890",
          fax: "+1234567899",
          email: "is.moilomiliy97@gmail.com",
          contactPerson: "Harry",
          contact: "+1234567892",
          companyRegistrationNo: "RC12345678",
          industry:"Sporting Goods"        
        },
          {
          approved: false,
          name: 'Sri KDU',
          address: "3, 5, 7, Jalan Teknologi 2/1,, Petaling Jaya, Malaysia",
          telephone: "+60361453888",
          fax: "+60361453686",
          email: "info@srikdu.edu.my",
          contactPerson: "Erik",
          contact: "+60361453285",
          companyRegistrationNo: "556354-A",
          industry:"Schools"        
        },
        {
          approved: false,
          name: 'Vertu',
          address: "2.53.00, Level 2, Kuala Lumpur, Malaysia",
          telephone: "+60321437878",
          fax: "+60321437875",
          email: "vertu78@gmail.com",
          contactPerson: "Owen",
          contact: "+60321437170",
          companyRegistrationNo: "qwer1234",
          industry:"Community & Social Services"        
        },
        {
          approved: false,
          name: 'Canon Malaysia Sdn Bhd',
          address: "6-2-01 Canon Tower, UOA Business Park (Tower 6), Kota Kinabalu, Malaysia",
          telephone: "088383889",
          fax: "088383809",
          email: "contactus@canon.com.my",
          contactPerson: "Tristan",
          contact: "088383686",
          companyRegistrationNo: "605946-T",
          industry:"Consumer Goods"        
        },
        {
          approved: false,
          name: 'Tune Protect',
          address: "T06-T08 3rd Floor Ipoh Parade",
          telephone: "+6052543561",
          fax: "+6052543260",
          email: "marketing@5g-gallery.com.m",
          contactPerson: "Victoria",
          contact: "+6052543866",
          companyRegistrationNo: "JP807577-U",
          industry:"Insurance"        
        },
      ],
      headers: [
        {
          text: 'Companies',
          align: 'start',
          sortable: false,
          value: 'name',
        },
        { text: 'Approved', value:'approved' },
        { text: 'Address', value:'address' },
        { text: 'Telephone', value:'telephone' },
        { text: 'Fax', value:'fax' },
        { text: 'Email', value:'email' },
        { text: 'Contact Person ', value:'contactPerson' },
        { text: 'Contact ', value:'contact' },
        { text: 'Registration No ', value:'companyRegistrationNo' },
        { text: 'Industry', value:'industry' },

      ],
      currentRow: {}
    }),
    methods: {
      showModal(row) {
        this.currentRow = row;
        this.dialog = true;
      },
      approve() {
        this.currentRow.approved = true;
      } 
    },
  }
</script>
<style scoped>
.check-circle {
  font-size: 20px;
  margin-left: 5px;
  color: #888;
}
.approved {
  color: green;
}
.dialog {
  font-size: 16px;
}
.card-infos {
  color: grey;
}
.card-details {
  color: black;
}
.check-circle {
  width: 20px;
  margin-left: 5px;
}
.headline {
  margin-bottom: 20px;
}
.elevation-1 {
  margin-top: 10px;
}
.card-section-top {
  display: flex;
  margin-bottom: 20px;
}
.card-section-middle {
  display: flex;
  margin-bottom: 20px;
}
.details-section {
  width: 50%;
}
.card-section-bottom {
  margin-bottom: 10px;
  display: flex;
}
i {
  margin-right: 5px;
}
.email-section,.call-section {
  margin-right: 30px;
}
.address-section {
  margin-bottom: -10px;
}
.approve-button {
  margin-right: 20px;
}
</style>