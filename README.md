How can update reCAPTCHA V2 to reCAPTCHA V3
Youtube: https://youtu.be/C69rVkgZ5ec

Step 1 – Install Google Recaptcha Package (anhskohbo/no-captcha)

 write in terminal composer require anhskohbo/no-captcha
 
Step 2 – Add the below code in config/app.php 
  Anhskohbo\NoCaptcha\NoCaptchaServiceProvider::class
  'NoCaptcha' => Anhskohbo\NoCaptcha\Facades\NoCaptcha::class
  
Step 3 – Add the below code in .env
  NOCAPTCHA_SITEKEY=secret_site_key
  NOCAPTCHA_SECRET=secret_key
  
Step 4 – open this site of Google to make a new secret Recaptcha
  https://www.google.com/recaptcha/admin/create
  
  Label:
  in this part write your web of Address. i use laravel
  
  in this part(reCAPTCHA type) choose reCAPTCHA v3 or reCAPTCHA v2
  
  in this part(Domains) write somethings like localhost.
  
Step 5 – open registerController and add 
 'g-recaptcha-response' => ['required', 'captcha'],
 
Step 6 – Add the below code in register blade like this,
  <div class="form-group">
                          <label for="captcha">Captcha</label>
                             {!! NoCaptcha::renderJs() !!}
                             {!! NoCaptcha::display() !!}
                                @error('g-recaptcha-response')
                            <div class="alert alert-danger mt-1 mb-1">{{ $message }}</div>
                               @enderror
                        </div> 
						
						

step 7. - write this script in template

<script src="https://www.google.com/recaptcha/api.js?onload=vueRecaptchaApiLoaded&render=explicit" async defer>


 thanks
