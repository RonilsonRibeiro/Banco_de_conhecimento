<strong>Firefox - Automatizando Certificados não seguros</strong>


Costuma ser um problema quando trabalhamos com automação de testes utilizando o browser Firefox e lidamos com páginas com certificados expirados. O GeckoDriver costuma fechar o driver quando se depara com a mensagem de erro, devolvendo uma falha no teste. Abaixo veremos como configurar a nossa env.rb para que o browser ignore as mensagens de falha na segurança.
</p>
<br>

Na env.rb configure o browser da seguinte forma: </p>
<blockquote>
			caps = Selenium::WebDriver::Remote::Capabilities.firefox <br>
			caps['acceptInsecureCerts'] = true <br>
			Capybara::Selenium::Driver.new(app, :browser => :firefox, marionette: true, desired_capabilities: caps)</p></p>
</blockquote>

Pronto! o seu firefox já está ignorando o erro de certificados não seguros.