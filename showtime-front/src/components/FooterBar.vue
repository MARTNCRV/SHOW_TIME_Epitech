<template>
  <footer>
    <div class="footer-dark">
      <div class="container">
        <div class="row">
          <div class="col-sm-6 col-md-3 item">
            <h3>Services</h3>
            <ul>
              <li><a href="#">Web design</a></li>
              <li><a href="#">Development</a></li>
              <li><a href="#">Hosting</a></li>
            </ul>
          </div>
          <div class="col-sm-6 col-md-3 item">
            <h3>About</h3>
            <ul>
              <li><a href="#">Company</a></li>
              <li><a href="#">Team</a></li>
              <li><a href="#">Careers</a></li>
            </ul>
          </div>
        </div>
        <p class="copyright">My Music team 2022</p>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  name: "FooterBar",
};
</script>

<style scoped>
.row {
  display: flex;
  justify-content: space-evenly;
  padding-top: 20px;
}
.footer-dark {
  padding: 50px 0;
  background-color: rgb(12, 11, 11);
  margin-top: 10px;
  width: 100%;
  height: 300px;
}
.footer-dark h3 {
  margin-top: 0;
  margin-bottom: 12px;
  font-weight: bold;
  font-size: 16px;
  color: #f0f9ff;
}
.footer-dark ul {
  padding: 0;
  list-style: none;
  line-height: 1.6;
  font-size: 14px;
  margin-bottom: 0;
}
.footer-dark ul a {
  color: #f0f9ff;
  text-decoration: none;
  opacity: 0.6;
}
.footer-dark ul a:hover {
  opacity: 0.8;
}
@media (max-width: 767px) {
  .footer-dark .item:not(.social) {
    text-align: center;
    padding-bottom: 20px;
  }
}
.footer-dark .item.text {
  margin-bottom: 36px;
}
@media (max-width: 767px) {
  .footer-dark .item.text {
    margin-bottom: 0;
  }
}
.footer-dark .item.text p {
  opacity: 0.6;
  margin-bottom: 0;
}
.item.social {
  text-align: right;
}
@media (max-width: 991px) {
  .footer-dark .item.social {
    text-align: center;
    margin-top: 20px;
  }
}
.footer-dark .item.social > a {
  font-size: 20px;
  width: 36px;
  height: 20px;
  line-height: 36px;
  display: inline-block;
  text-align: center;
  border-radius: 50%;
  box-shadow: 0 0 0 1px rgba(255, 255, 255, 0.4);
  margin: 0 8px;
  color: rgb(212, 146, 146);
  opacity: 0.75;
}
.footer-dark .item.social > a:hover {
  opacity: 0.9;
}
.footer-dark .copyright {
  text-align: center;
  padding-top: 24px;
  opacity: 0.3;
  font-size: 13px;
  margin-bottom: 0;
}
.footer-bar {
  height: 20px;
}
</style>
