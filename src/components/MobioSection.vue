<template>
  <section class="mobio-section">
    <div class="container">
      <!-- Section 1: ACTIVATION CDP -->
      <div class="section-item">
        <div class="image-container">
          <img src="/hero-image-1-60162a.png" alt="Activation CDP" class="featured-image" />
        </div>
        <div class="content-container">
          <div class="vertical-divider"></div>
          <div class="number-circle">01</div>
          <div class="tag-button primary-tag">ACTIVATION CDP</div>
          <h2 class="section-title">A Comprehensive Platform to meets the Goals of every Marketer</h2>
          <div class="team-info">
            <img src="/src/assets/96-page-speed.svg" alt="Marketing Team Icon" class="team-icon" />
            <span class="team-text">For Marketing Team</span>
          </div>
          <div class="feature-tags">
            <span class="feature-tag">Omnichannel Journey</span>
            <span class="feature-tag">OnPage Journey</span>
            <span class="feature-tag">Segmentation</span>
            <span class="feature-tag">Personalization</span>
            <span class="feature-tag">Email Builder</span>
            <span class="feature-tag">Popup Builder</span>
            <span class="feature-tag">Landing Page Builder</span>
            <span class="feature-tag">A/B Testing</span>
            <span class="feature-tag">Ads Audience Sync</span>
            <span class="feature-tag">Marketing Report</span>
          </div>
          <button class="explore-button primary-button">
            Explore More
            <img src="/src/assets/hero-line.svg" alt="Arrow Icon" class="arrow-icon" />
          </button>
        </div>
      </div>

      <!-- Section 2: SMART CRM -->
      <div class="section-item">
        <div class="image-container">
          <img src="/hero-image-2-60162a.png" alt="Smart CRM" class="featured-image" />
        </div>
        <div class="content-container">
          <div class="vertical-divider"></div>
          <div class="number-circle">02</div>
          <div class="tag-button secondary-tag">SMART CRM</div>
          <h2 class="section-title">Elevate Sales, Delight Service Empowering Teams for Seamless Success</h2>
          <div class="team-info">
            <img src="/src/assets/custom-domain.svg" alt="Sales & Service Team Icon" class="team-icon" />
            <span class="team-text">For Sales & Service Team</span>
          </div>
          <div class="feature-tags">
            <span class="feature-tag">Oppty Management</span>
            <span class="feature-tag">Sales Pipeline</span>
            <span class="feature-tag">Survey</span>
            <span class="feature-tag">Call Center</span>
            <span class="feature-tag">Smart Routing</span>
            <span class="feature-tag">Social & Chat</span>
            <span class="feature-tag">Ticket Management</span>
            <span class="feature-tag">Automation Process</span>
            <span class="feature-tag">Workflow Management</span>
            <span class="feature-tag">Task Management</span>
            <span class="feature-tag">KPI Management</span>
            <span class="feature-tag">Sales & Service Dashboard</span>
          </div>
          <button class="explore-button secondary-button">
            Explore More
            <img src="/src/assets/hero-line.svg" alt="Arrow Icon" class="arrow-icon" />
          </button>
        </div>
      </div>

      <!-- Section 3: ANALYTICS DATA PLATFORM (ADP) -->
      <div class="section-item">
        <div class="image-container">
          <img src="/hero-image-3-60162a.png" alt="Analytics Data Platform" class="featured-image" />
        </div>
        <div class="content-container">
          <div class="vertical-divider"></div>
          <div class="number-circle">03</div>
          <div class="tag-button tertiary-tag">ANALYTICS DATA PLATFORM (ADP)</div>
          <h2 class="section-title">Unleash the Power of Your Data, Make Smarter Business Decisions</h2>
          <div class="team-info">
            <img src="/src/assets/devices.svg" alt="Data & Digital Team Icon" class="team-icon" />
            <span class="team-text">For Data & Digital Team</span>
          </div>
          <div class="feature-tags">
            <span class="feature-tag">RFM Analysis</span>
            <span class="feature-tag">Customer Lifetime Value</span>
            <span class="feature-tag">Prospensity Model</span>
            <span class="feature-tag">Next Best Offering</span>
            <span class="feature-tag">Data Studio for BI</span>
            <span class="feature-tag">Deep Report</span>
          </div>
          <button class="explore-button tertiary-button">
            Explore More
            <img src="/src/assets/hero-line.svg" alt="Arrow Icon" class="arrow-icon" />
          </button>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
</script>

<style scoped>
.mobio-section {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 150px 25px 0px;
  width: 100%;
  box-sizing: border-box;
  background-color: #FFFFFF; /* fill_HJE2C3 */
}

.container {
  display: flex;
  flex-direction: column;
  gap: 100px; /* Khoảng cách giữa các section-item */
  width: 1230px; /* layout_VZDLGE width */
  max-width: 100%;
}

.section-item {
  display: flex;
  flex-direction: row;
  align-items: stretch;
  gap: 0; /* Reset gap for inner flex items */
  height: 598.39px; /* layout_E21F1T height for first section, will adjust for others */
  background-color: #FFFFFF; /* fill_HJE2C3 */
  position: relative;
}

.section-item:nth-child(2) {
  height: 694.39px; /* layout_YI5S5E height for second section */
}

.section-item:nth-child(3) {
  height: 478.39px; /* layout_5PHCQ2 height for third section */
}

.image-container {
  flex: 1;
  display: flex;
  justify-content: flex-end;
  align-items: center;
  padding-right: 15px; /* layout_QG2WKJ padding */
}

.featured-image {
  width: 575px; /* layout_LPBI4R width */
  height: 431.59px; /* layout_LPBI4R height */
  object-fit: fill;
}

.content-container {
  display: flex;
  flex-direction: column;
  gap: 16px;
  padding-left: 96px; /* layout_1KCWRD padding */
  flex: 1;
  position: relative;
  justify-content: center;
}

.vertical-divider {
  position: absolute;
  left: 48px; /* layout_0MVOL4 x */
  top: 0;
  width: 2px; /* layout_BTOLTB width */
  height: 100%; /* layout_BTOLTB height */
  background-color: #D3E2FD; /* fill_9FZ367 */
}

.number-circle {
  position: absolute;
  left: 17px; /* 48px (left of content-container) - 31px (offset from divider) */
  top: 267.19px; /* layout_BO8G7T y */
  width: 42px; /* layout_TPUXSD width */
  height: 42px; /* layout_TPUXSD height */
  border-radius: 50%;
  background-color: #DBE8FF; /* fill_DYHAOA */
  display: flex;
  justify-content: center;
  align-items: center;
  font-family: Poppins;
  font-weight: 500;
  font-size: 20px;
  color: #226FF5; /* fill_4XUTO9 */
  z-index: 1; /* Ensure it's above the divider */
}

.section-item:nth-child(2) .number-circle {
  top: 315.19px; /* layout_D4K24E y */
  background-color: #DBE8FF; /* fill_DYHAOA */
  color: #03A0A0; /* fill_M1YC0K */
}

.section-item:nth-child(3) .number-circle {
  top: 218.19px; /* layout_HUZL8U y */
  background-color: #DBE8FF; /* fill_DYHAOA */
  color: #387DF6; /* fill_H9GEHI */
}

.tag-button {
  display: inline-flex;
  padding: 9.5px 20px 9.89px;
  border-radius: 8px;
  font-family: Poppins;
  font-weight: 500;
  font-size: 17.6px;
  line-height: 1.5em;
  text-align: left;
  align-items: center;
  justify-content: center;
  white-space: nowrap;
}

.primary-tag {
  background-color: #226FF5; /* fill_4XUTO9 */
  color: #FFFFFF; /* fill_HJE2C3 */
}

.secondary-tag {
  background-color: #03A0A0; /* fill_M1YC0K */
  color: #FFFFFF; /* fill_HJE2C3 */
}

.tertiary-tag {
  background: linear-gradient(to bottom right, #387DF6 2.35%, #6B43C2 97.65%); /* fill_RJ91GD */
  color: #FFFFFF; /* fill_HJE2C3 */
}

.section-title {
  font-family: Poppins;
  font-weight: 600;
  font-size: 24px;
  line-height: 1.5em;
  color: #1C232F; /* fill_6HZ0XQ */
  margin: 0;
}

.team-info {
  display: flex;
  align-items: center;
  padding-top: 16px;
}

.team-icon {
  width: 32px;
  height: 32px;
  object-fit: contain;
}

.team-text {
  font-family: Poppins;
  font-weight: 400;
  font-size: 16px;
  line-height: 1.5em;
  color: #226FF5; /* fill_4XUTO9 */
  margin-left: 10px; /* layout_E7C4W5 padding */
}

.section-item:nth-child(2) .team-text {
  color: #03A0A0; /* fill_M1YC0K */
}

.section-item:nth-child(3) .team-text {
  color: #387DF6; /* fill_H9GEHI */
}

.feature-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 12px; /* Khoảng cách giữa các feature tags */
  margin-top: 16px; /* Adjust as needed based on Figma */
}

.feature-tag {
  display: inline-flex;
  padding: 12px 16px;
  border-radius: 8px;
  background-color: #F4F8FF; /* fill_AKI0NN */
  font-family: Poppins;
  font-weight: 500;
  font-size: 16px;
  line-height: 1.5em;
  color: #1C232F; /* fill_6HZ0XQ */
  white-space: nowrap;
}

.explore-button {
  display: flex;
  align-items: center;
  gap: 16px; /* layout_AUJ953 padding */
  padding: 31.5px 0px 0px; /* layout_73MVD2 padding */
  background: none;
  border: none;
  cursor: pointer;
  font-family: Poppins;
  font-weight: 500;
  font-size: 16px;
  line-height: 1.5em;
  text-align: left;
}

.primary-button {
  color: #226FF5; /* fill_4XUTO9 */
}

.secondary-button {
  color: #03A0A0; /* fill_M1YC0K */
}

.tertiary-button {
  color: #387DF6; /* fill_H9GEHI */
}

.arrow-icon {
  width: 24px; /* layout_O1S92Y width */
  height: 24px; /* layout_O1S92Y height */
  object-fit: contain;
}
</style>