<strong>Firefox - Automatizando Certificados n�o seguros</strong>


Costuma ser um problema quando trabalhamos com automa��o de testes utilizando o browser Firefox e lidamos com p�ginas com certificados expirados. O GeckoDriver costuma fechar o driver quando se depara com a mensagem de erro, devolvendo uma falha no teste. Abaixo veremos como configurar a nossa env.rb para que o browser ignore as mensagens de falha na seguran�a.
</p>
<br>

Na env.rb configure o browser da seguinte forma: </p>
<blockquote>
			caps = Selenium::WebDriver::Remote::Capabilities.firefox <br>
			caps['acceptInsecureCerts'] = true <br>
			Capybara::Selenium::Driver.new(app, :browser => :firefox, marionette: true, desired_capabilities: caps)</p></p>
</blockquote>

Pronto! o seu firefox j� est� ignorando o erro de certificados n�o seguros.