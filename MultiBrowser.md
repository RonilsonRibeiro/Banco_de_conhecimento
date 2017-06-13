<strong>Configuração da Env.rb para o uso de multi Browser </strong>

Quando estamos testando é comum precisarmos fazer testes em mais de um browser, o que pode ser um problema para alguns testers. Abaixo iremos ver como configurar seu env.rb para suportar varios navegadores e como criar um profile para facilitar a chamada do browser.</p>

Primeiramente é necessário fazer a configuração da sua env.rb com o register driver: </p>

<blockquote>
Capybara.register_driver :selenium do |app|
 
    if BROWSER.eql?('chrome')
        Capybara::Selenium::Driver.new(app,:browser => :chrome,
            :desired_capabilities => Selenium::WebDriver::Remote::Capabilities.chrome(
                'chromeOptions' => {
                    'args' => [ "--start-maximized" ]}
            )
        )
    elsif BROWSER.eql?('firefox')
        caps = Selenium::WebDriver::Remote::Capabilities.firefox
        caps['acceptInsecureCerts'] = true
        Capybara::Selenium::Driver.new(app, :browser => :firefox, marionette: true,
        desired_capabilities: caps)

    elsif BROWSER.eql?('iexplorer')
        Capybara::Selenium::Driver.new(app, :browser => :internet_explorer)

    elsif BROWSER.eql?('edge')
        Capybara::Selenium::Driver.new(app, :browser => :edge)

    elsif BROWSER.eql?('safari')
       Capybara::Selenium::Driver.new(app, :browser => :safari)

    elsif BROWSER.eql?('headless')
        options = {
            :js_errors => false
        }
        Capybara::Poltergeist::Driver.new(app, options)
    end
end
</blockquote>
