# tours-and-travels-2<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Tours, Travels & Tickets Booking</title>
<style>
  body {
    font-family: Arial, sans-serif;
    background: #f0f8ff;
    color: #003366;
    margin: 0;
    padding: 20px;
  }
  h1 {
    color: #0077cc;
    text-align: center;
  }
  /* Tabs container */
  .tabs {
    display: flex;
    justify-content: center;
    margin-bottom: 20px;
  }
  .tab-button {
    background: #0077cc;
    color: white;
    border: none;
    padding: 10px 20px;
    margin: 0 5px;
    cursor: pointer;
    border-radius: 6px 6px 0 0;
    font-weight: bold;
  }
  .tab-button.active {
    background: #005fa3;
  }
  /* Forms container */
  .form-container {
    max-width: 600px;
    margin: 0 auto;
    background: white;
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0 0 10px #aaccee;
  }
  /* Common form styles */
  label {
    font-weight: bold;
    display: block;
    margin-top: 15px;
  }
  input[type="text"],
  input[type="tel"],
  input[type="number"],
  select,
  textarea {
    width: 100%;
    padding: 8px;
    margin-top: 6px;
    border-radius: 4px;
    border: 1px solid #0077cc;
    box-sizing: border-box;
  }
  textarea {
    resize: vertical;
    height: 60px;
  }
  button.submit-btn {
    margin-top: 20px;
    background-color: #0077cc;
    border: none;
    color: white;
    padding: 12px 20px;
    text-align: center;
    font-size: 16px;
    border-radius: 6px;
    cursor: pointer;
    width: 100%;
  }
  button.submit-btn:hover {
    background-color: #005fa3;
  }
  small {
    color: #333;
  }
  .hidden {
    display: none;
  }
</style>
</head>
<body>
<h1>Tours, Travels & Tickets Booking</h1>
<div class="tabs">
  <button class="tab-button active" data-tab="tours">Tours</button>
  <button class="tab-button" data-tab="travels">Travels</button>
  <button class="tab-button" data-tab="tickets">Tickets</button>
</div>

<div class="form-container">
  
  <!-- Tours Form -->
  <form id="tours" class="booking-form">
    <label for="tours-name">Name *</label>
    <input type="text" id="tours-name" name="name" required>

    <label for="tours-mobile">Mobile Number *</label>
    <input type="tel" id="tours-mobile" name="mobile" pattern="[0-9]{10}" required placeholder="10 digit mobile number">

    <label for="tours-type">Tour Type *</label>
    <select id="tours-type" name="tourType" required>
      <option value="">Select</option>
      <option value="Monthly Tour">Monthly Tour</option>
      <option value="Family Tour">Family Tour</option>
      <option value="Couple Tour">Couple Tour</option>
      <option value="Daily Tour">Daily Tour</option>
    </select>

    <label for="tours-persons">Number of Persons *</label>
    <input type="number" id="tours-persons" name="persons" min="1" max="20" required>

    <label for="tours-address">Address *</label>
    <textarea id="tours-address" name="address" placeholder="Address / Pickup point" required></textarea>

    <label for="tours-message">Additional Details / Message</label>
    <textarea id="tours-message" name="message" placeholder="Special requests"></textarea>

    <button type="submit" class="submit-btn">Submit via WhatsApp</button>
  </form>

  <!-- Travels Form -->
  <form id="travels" class="booking-form hidden">
    <label for="travels-name">Name *</label>
    <input type="text" id="travels-name" name="name" required>

    <label for="travels-mobile">Mobile Number *</label>
    <input type="tel" id="travels-mobile" name="mobile" pattern="[0-9]{10}" required placeholder="10 digit mobile number">

    <label for="travels-type">Travel Type *</label>
    <select id="travels-type" name="travelType" required onchange="showVehicle(this.value)">
      <option value="">Select</option>
      <option value="Self Travel">Self Travel</option>
      <option value="Travel With Driver">Travel With Driver</option>
    </select>

    <div id="vehicle-section" class="hidden">
      <label for="vehicle-type">Vehicle Type *</label>
      <select id="vehicle-type" name="vehicleType">
        <option value="">Select</option>
        <option value="Bike">Bike</option>
        <option value="Auto">Auto</option>
        <option value="Car">Car</option>
        <option value="Bus">Bus</option>
        <option value="Tempo">Tempo</option>
        <option value="Taxi">Taxi</option>
      </select>
    </div>

    <label for="travels-from">From (Place) *</label>
    <input type="text" id="travels-from" name="from" required>

    <label for="travels-to">To (Place) *</label>
    <input type="text" id="travels-to" name="to" required>

    <label for="travels-address">Address *</label>
    <textarea id="travels-address" name="address" placeholder="Pickup point / address" required></textarea>

    <label for="travels-message">Additional Details / Message</label>
    <textarea id="travels-message" name="message" placeholder="Special requests"></textarea>

    <button type="submit" class="submit-btn">Submit via WhatsApp</button>
  </form>

  <!-- Tickets Form -->
  <form id="tickets" class="booking-form hidden">
    <label for="tickets-name">Name *</label>
    <input type="text" id="tickets-name" name="name" required>

    <label for="tickets-mobile">Mobile Number *</label>
    <input type="tel" id="tickets-mobile" name="mobile" pattern="[0-9]{10}" required placeholder="10 digit mobile number">

    <label for="tickets-travel-from">From (Place) *</label>
    <input type="text" id="tickets-travel-from" name="from" required>

    <label for="tickets-travel-to">To (Place) *</label>
    <input type="text" id="tickets-travel-to" name="to" required>

    <label for="tickets-address">Address *</label>
    <textarea id="tickets-address" name="address" placeholder="Address / Pickup point" required></textarea>

    <label for="tickets-message">Additional Details / Message</label>
    <textarea id="tickets-message" name="message" placeholder="Special requests"></textarea>

    <button type="submit" class="submit-btn">Submit via WhatsApp</button>
  </form>
</div>

<script>
  // Tab navigation
  const tabs = document.querySelectorAll('.tab-button');
  const forms = document.querySelectorAll('.booking-form');
  
  tabs.forEach(tab => {
    tab.addEventListener('click', () => {
      // Remove active class from all
      tabs.forEach(t => t.classList.remove('active'));
      // Hide all forms
      forms.forEach(f => f.classList.add('hidden'));
      
      // Activate current tab and show form
      tab.classList.add('active');
      document.getElementById(tab.getAttribute('data-tab')).classList.remove('hidden');
    });
  });

  // Show vehicle section conditionally in Travels form
  function showVehicle(value) {
    const vehicleSection = document.getElementById('vehicle-section');
    const vehicleTypeInput = document.getElementById('vehicle-type');
    if (value === 'Self Travel') {
      vehicleSection.classList.remove('hidden');
      vehicleTypeInput.setAttribute('required', 'required');
    } else {
      vehicleSection.classList.add('hidden');
      vehicleTypeInput.removeAttribute('required');
    }
  }

  // WhatsApp submit for all forms
  const bookingForms = document.querySelectorAll('.booking-form');
  bookingForms.forEach(form => {
    form.addEventListener('submit', function(event) {
      event.preventDefault();
      const formData = new FormData(form);

      // Build message based on form ID
      let msg = "*Booking Request*%0A";

      if (form.id === 'tours') {
        msg += `Category: Tours%0A`;
        msg += `Name: ${encodeURIComponent(formData.get('name'))}%0A`;
        msg += `Mobile: ${encodeURIComponent(formData.get('mobile'))}%0A`;
        msg += `Tour Type: ${encodeURIComponent(formData.get('tourType'))}%0A`;
        msg += `Number of Persons: ${encodeURIComponent(formData.get('persons'))}%0A`;
        msg += `Address: ${encodeURIComponent(formData.get('address'))}%0A`;
        msg += `Additional Details: ${encodeURIComponent(formData.get('message') || 'None')}`;
      } else if (form.id === 'travels') {
        msg += `Category: Travels%0A`;
        msg += `Name: ${encodeURIComponent(formData.get('name'))}%0A`;
        msg += `Mobile: ${encodeURIComponent(formData.get('mobile'))}%0A`;
        msg += `Travel Type: ${encodeURIComponent(formData.get('travelType'))}%0A`;
        let vehicleType = formData.get('vehicleType') || 'N/A';
        msg += `Vehicle Type: ${encodeURIComponent(vehicleType)}%0A`;
        msg += `From: ${encodeURIComponent(formData.get('from'))}%0A`;
        msg += `To: ${encodeURIComponent(formData.get('to'))}%0A`;
        msg += `Address: ${encodeURIComponent(formData.get('address'))}%0A`;
        msg += `Additional Details: ${encodeURIComponent(formData.get('message') || 'None')}`;
      } else if (form.id === 'tickets') {
        msg += `Category: Tickets%0A`;
        msg += `Name: ${encodeURIComponent(formData.get('name'))}%0A`;
        msg += `Mobile: ${encodeURIComponent(formData.get('mobile'))}%0A`;
        msg += `From: ${encodeURIComponent(formData.get('from'))}%0A`;
        msg += `To: ${encodeURIComponent(formData.get('to'))}%0A`;
        msg += `Address: ${encodeURIComponent(formData.get('address'))}%0A`;
        msg += `Additional Details: ${encodeURIComponent(formData.get('message') || 'None')}`;
      }

      const whatsappNumber = '919877143043';
      const whatsappURL = `https://wa.me/${whatsappNumber}?text=${msg}`;

      window.open(whatsappURL, '_blank');
    });
  });
</script>
</body>
</html>
